FROM elixir:1.6-slim

LABEL maintainer="Varlog <varlog.err@gmail.com>"

ENV TINI_VERSION=v0.16.1 \
    THE_USER=elixir \
    THE_GROUP=elixir \
    THE_HOME=/home/elixir

ARG THE_USER_ID=1000
ARG THE_GROUP_ID=1000

ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /sbin/tini

RUN chmod +x /sbin/tini

# create elixir user
RUN addgroup -q --gid $THE_GROUP_ID $THE_GROUP \
    && adduser -q --disabled-login \
      --ingroup $THE_GROUP \
      --shell /bin/bash --gecos ",,," \
      --home $THE_HOME \
      --uid $THE_USER_ID $THE_USER

RUN apt-get update \
    && apt-get install -y openssl

ENTRYPOINT ["/sbin/tini", "--"]
CMD :

USER ${THE_USER}
RUN mix local.hex --force
