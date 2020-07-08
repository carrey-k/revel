FROM golang:1.14

LABEL maintainer="460876880@qq.com"

ENV GOPATH /go
ENV HTTP_PROXY "http://7.40.23.198:3128"
ENV HTTPS_PROXY "http://7.40.23.198:3128"

RUN set -x \
    && go get -v github.com/revel/revel \
    && go get -v github.com/revel/cmd/revel

# clear apt cache and remove unnecessary packages
# RUN apt-get autoclean && apt-get -y autoremove

WORKDIR $GOPATH
EXPOSE 9000
