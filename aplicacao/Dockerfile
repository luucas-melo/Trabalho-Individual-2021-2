FROM ruby:3.0.0
RUN apt-get update && \
        apt-get -qq -y install netcat-openbsd curl && \
        curl -sL https://deb.nodesource.com/setup_14.x | bash - &&\
        apt-get install -y nodejs
RUN npm i -g yarn
WORKDIR /aplicacao
RUN gem install bundler
COPY . .
RUN bundle install

COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

CMD bash -c "rails assets:precompile; rails db:setup; rails server -b 0.0.0.0"
