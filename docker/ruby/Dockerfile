FROM ruby:2.5-slim-stretch

LABEL maintainer="Varlog <varlog.err@gmail.com>"

ENV TINI_VERSION=v0.16.1 \
    THE_USER=ruby \
    THE_GROUP=ruby \
    THE_HOME=/home/ruby

ARG THE_USER_ID=1000
ARG THE_GROUP_ID=1000

ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /sbin/tini

RUN chmod +x /sbin/tini

# create ruby user
RUN addgroup -q --gid $THE_GROUP_ID $THE_GROUP \
    && adduser -q --disabled-login \
      --ingroup $THE_GROUP \
      --shell /bin/bash --gecos ",,," \
      --home $THE_HOME \
      --uid $THE_USER_ID $THE_USER

ENTRYPOINT ["/sbin/tini", "--"]
CMD :

USER ${THE_USER}
