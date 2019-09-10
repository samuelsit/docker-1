FROM debian:8

RUN apt-get update && apt-get upgrade -y && apt-get install -y openssh-server ca-certificates postfix wget

RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && chmod +x script.deb.sh

RUN bash script.deb.sh

RUN apt-get install -y gitlab-ce

RUN mkdir -p /etc/gitlab/ssl
RUN chmod 700 /etc/gitlab/ssl
RUN openssl req \
			-x509 \
			-days 365 \
			-newkey rsa:2048 -nodes \
			-keyout /etc/gitlab/ssl/ruru.gitlab.key \
			-out /etc/gitlab/ssl/ruru.gitlab.crt \
			-subj "/C=FR/ST=IDF/L=Paris/O=42/CN=www.ruru.gitlab.com"

RUN echo "external_url \"https://ruru.gitlab.com\"" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['ssl_certificate'] = \"/etc/gitlab/ssl/ruru.gitlab.crt\"" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['ssl_certificate_key'] = \"/etc/gitlab/ssl/ruru.gitlab.key\"" >> /etc/gitlab/gitlab.rb

EXPOSE 22 80 443

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && service ssh start && gitlab-ctl reconfigure && gitlab-ctl tail
