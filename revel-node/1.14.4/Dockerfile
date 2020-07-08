FROM ubuntu:18.04

MAINTAINER Chengkun Kang <chengkun.kang@sanofi.com>

ENV HTTP_PROXY "http://7.40.23.198:3128"
ENV HTTPS_PROXY "http://7.40.23.198:3128"

# Install libraries
RUN apt-get update -qq \
    && apt-get install -yq cmake \
                           fceux \
                           gcc \
                           libboost-all-dev \
                           libjpeg-dev \
                           libsdl2-dev \
                           make \
                           unzip \
                           wget \
                           zlib1g-dev \
                           supervisor \
                           git \
                           curl \
                           mercurial \
                           nodejs
                        

# Install go tarball
ENV GOLANG_VERSION 1.14.4
RUN wget -qO- http://golang.org/dl/go${GOLANG_VERSION}.linux-amd64.tar.gz | tar -C /usr/local -xzf -

# Set PATHS for GOLANG 
ENV HOME /root
RUN mkdir ${HOME}/go
ENV GOPATH ${HOME}/go
ENV PATH ${PATH}:${GOPATH}/bin:/usr/local/go/bin

WORKDIR ${HOME}

# Install revel framework 
RUN go get -u github.com/revel/revel
RUN go get -u github.com/revel/cmd/revel

# Define mountable directories.
VOLUME ${HOME}/go
VOLUME ["/etc/supervisor/conf.d"]

WORKDIR ${HOME}/go

# clear apt cache and remove unnecessary packages
RUN apt-get autoclean && apt-get -y autoremove

EXPOSE 9000

CMD ["supervisord", "-c", "/etc/supervisor/supervisord.conf"]
