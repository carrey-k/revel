FROM golang:1.14

MAINTAINER Chengkun Kang <chengkun.kang@sanofi.com>

ENV GOPATH /go
ENV HTTP_PROXY "http://7.40.23.198:3128"
ENV HTTPS_PROXY "http://7.40.23.198:3128"

RUN set -x \
    && go get -v github.com/revel/revel \
    && go get -v github.com/revel/cmd/revel

# Install node
ENV NODE_VERSION "14.5.0"
ENV NODE_ZIP "node-v$NODE_VERSION-linux-x64.tar.xz"

RUN wget -P downloads https://nodejs.org/dist/v$NODE_VERSION/$NODE_ZIP && \
    tar -C /usr/local --strip-components 1 -xJf downloads/$NODE_ZIP && \
    rm -rf downloads

# clear apt cache and remove unnecessary packages
# RUN apt-get autoclean && apt-get -y autoremove

WORKDIR $GOPATH
EXPOSE 9000
