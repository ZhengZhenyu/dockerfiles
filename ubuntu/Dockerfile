FROM ubuntu:bionic

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN apt-get -q update \
    && apt-get -q install -y --no-install-recommends \
        vim \
        build-essential \
        autoconf \
        automake \
        libtool \
        cmake \
        zlib1g-dev \
        pkg-config \
        libssl-dev \
        libssl1.0.0 \
        libsasl2-dev \
        bats \
        curl \
        sudo \
        git \
        libgnutls28-dev \
        libnl-3-dev \
        libnl-route-3-dev \
        libxml2-dev \
        libdevmapper-dev \
        libpciaccess-dev \
        uuid-dev \
        ca-certificates

WORKDIR /opt
