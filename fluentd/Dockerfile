FROM ruby:2.4.1-alpine

LABEL maintainer "yvarbanov"

RUN apk add --no-cache build-base

RUN gem install fluentd -v "~> 0.12.0" --no-ri --no-rdoc

COPY fluent.conf /fluentd/etc/

CMD fluentd -c /fluentd/etc/fluent.conf
