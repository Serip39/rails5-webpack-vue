FROM ruby:2.6.3-alpine

ENV LANG C.UTF-8
ENV WORKSPACE=/app

# 基本モジュールインストール
RUN apk update && \
  apk add --no-cache tzdata libxml2-dev curl-dev make gcc libc-dev build-base libxslt-dev g++ mariadb-dev less && \
  rm -rf /usr/local/bundle/cache/* /usr/local/share/.cache/* /var/cache/* /tmp/* && \
  apk del libxml2-dev curl-dev make gcc libc-dev g++

# 時刻設定
RUN apk --update add tzdata && \
  rm -rf /var/cache/apk/*
ENV TZ Asia/Tokyo

# node + yarn
# python2はnodeインストール時の依存関係
RUN apk add --no-cache alpine-sdk \
  nodejs-current \
  nodejs-npm \
  yarn \
  python2

RUN mkdir -p $WORKSPACE
WORKDIR $WORKSPACE

# ADD Gemfile $WORKSPACE/Gemfile
# ADD Gemfile.lock $WORKSPACE/Gemfile.lock

# RUN bundle install

COPY . $WORKSPACE

# Start the main process.
# CMD ["rails", "server", "-b", "0.0.0.0"]
