FROM debian:8

RUN apt-get update && apt-get upgrade -y && apt-get install -y openssh-server ca-certificates postfix wget

RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && chmod +x script.deb.sh

RUN bash script.deb.sh

RUN apt-get install -y gitlab-ce

RUN mkdir -p /etc/gitlab/ssl && \
	chmod 700 /etc/gitlab/ssl && \
	openssl req -new -x509 -nodes -newkey rsa:2048 -keyout /etc/gitlab/ssl/gitlab.key -out /etc/gitlab/ssl/gitlab.crt -days 365 -subj /CN=192.168.99.100

RUN echo "external_url \"https://192.168.99.100\"" >> /etc/gitlab/gitlab.rb

RUN echo "nginx['ssl_certificate'] = \"/etc/gitlab/ssl/gitlab.crt\"" >> /etc/gitlab/gitlab.rb

RUN echo "nginx['ssl_certificate_key'] = \"/etc/gitlab/ssl/gitlab.key\"" >> /etc/gitlab/gitlab.rb

RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 22" >> /etc/gitlab/gitlab.rb

EXPOSE 22 443

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && service ssh start && gitlab-ctl reconfigure && gitlab-ctl tail
