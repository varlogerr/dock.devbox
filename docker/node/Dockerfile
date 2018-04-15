FROM node:9.11-slim

LABEL maintainer="Varlog <varlog.err@gmail.com>"

ENV TINI_VERSION=v0.16.1
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /sbin/tini
RUN chmod +x /sbin/tini

ADD assets/.npmrc /home/node/
RUN \
    chown node:node /home/node/.npmrc \
    && echo "PATH=$PATH:/modules/bin" >> /home/node/.bashrc

ENTRYPOINT ["/sbin/tini", "--"]
CMD :

USER node
