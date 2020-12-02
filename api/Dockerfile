FROM ruby:2.5.7

RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs
RUN mkdir /rails_api

WORKDIR /rails_api

ADD Gemfile /rails_api
ADD Gemfile.lock /rails_api

RUN gem install bundler rails rake

RUN bundle install
COPY . .

EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]
