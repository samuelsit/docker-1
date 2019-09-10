# docker build -t ft-rails:on-build .
# git clone https://bitbucket.org/railstutorial/sample_app_4th_ed.git sample_app_reference
# Changer la version de rake a 12.3.2 dans Gemfile.lock
# docker build .
# docker run -it --rm -p 3000:3000 <image id>

FROM ruby

RUN apt-get update && apt-get upgrade -y && apt-get install rails -y && mkdir -p /opt/app

ONBUILD WORKDIR /opt/app

ONBUILD ADD . /opt/app

ONBUILD EXPOSE 3000

ONBUILD RUN bundle install

ONBUILD RUN rake db:migrate

ONBUILD RUN rake db:seed
