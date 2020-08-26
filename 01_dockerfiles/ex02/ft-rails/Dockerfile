FROM ruby:latest
RUN apt-get update -y && apt-get install -y build-essential libpq-dev nodejs sqlite3 gem
RUN gem install bundler:1.16.2
RUN gem install rails --no-document
RUN gem install rake -v 12.3.1 --no-document

ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app

ONBUILD EXPOSE 3000
ONBUILD RUN bundle install
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed

# docker build -t ft-rails:on-build .
