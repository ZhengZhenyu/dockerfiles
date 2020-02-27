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

RUN useradd -m -d /home/kevin -s /bin/bash kevin && echo kevin:kevin | chpasswd && adduser kevin sudo
RUN echo "kevin ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

USER kevin
WORKDIR /home/kevin
