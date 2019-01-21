FROM ruby

RUN apt-get update && \
apt-get install mysql-client sqlite3 nodejs -y && \
gem install rails && \
mkdir -p /opt/app

WORKDIR /opt/app

ONBUILD ADD app /opt/app

ONBUILD RUN bundle update && \
bundle install && \
rake db:migrate && \
rake db:seed

# docker build -t ft-rails:on-build .
# git clone https://github.com/mjhea0/rails-helloworld.git app
# docker build -t ex02 .
# docker run -it --rm -p 3000:3000 ex02
