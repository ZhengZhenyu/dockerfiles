FROM ubuntu:bionic

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN apt-get -q update \
    && apt-get -q install -y --no-install-recommends \
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
        openjdk-8-jdk \
        maven \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-arm64

RUN useradd -m -d /home/hive -s /bin/bash hive && echo hive:hive | chpasswd && adduser hive sudo
#RUN echo "hive ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Build Hadoop Before play with Hive
#RUN curl -sL https://github.com/liusheng/package/releases/download/protobuf-aarch64/protobuf-3.7.1.tar.gz | tar zx -C /opt/
#RUN echo "/opt/protobuf-3.7.1/lib/" > /etc/ld.so.conf.d/protobuf-3.7.1.conf && ldconfig
#ENV PROTOBUF_HOME /opt/protobuf-3.7.1
#ENV PATH "${PATH}:/opt/protobuf-3.7.1/bin"

USER hive
WORKDIR /home/hive

#RUN curl -sL https://github.com/liusheng/package/files/3904116/wildfly-openssl-1.0.7.Final.jar.tar.gz | tar zx \
#    && mvn install:install-file -DgroupId=org.wildfly.openssl -Dfile=wildfly-openssl-1.0.7.Final.jar -DartifactId=wildfly-openssl -Dversion=1.0.7.Final -Dpackaging=jar \
#    && rm wildfly-openssl-1.0.7.Final.jar

#RUN curl -sL https://github.com/liusheng/package/releases/download/netty-all/netty-all-4.1.27-linux-aarch64.jar.tar.gz | tar zx \
#    && mvn install:install-file -DgroupId=io.netty -Dfile=netty-all-4.1.27-linux-aarch64.jar -DartifactId=netty-all -Dversion=4.1.27.Final -Dpackaging=jar \
#    && rm netty-all-4.1.27-linux-aarch64.jar
    
#RUN git clone https://github.com/apache/hadoop \
#    && cd hadoop \
#    && mvn clean install -e -B -Pdist,native -Dtar -DskipTests -Dmaven.javadoc.skip 2>&1

# Play with Hive

#USER root

#RUN curl -sL https://github.com/liusheng/package/releases/download/protobuf-aarch64/protobuf-2.5.0.tar.gz | tar zx -C /opt/
#RUN echo /opt/protobuf-2.5.0/lib/ > /etc/ld.so.conf.d/protobuf-2.5.0.conf && ldconfig
#ENV PROTOBUF_HOME /opt/protobuf-2.5.0
#ENV PATH "${PATH}:/opt/protobuf-2.5.0/bin"

#USER hive

#RUN mvn install:install-file -DgroupId=com.google.protobuf -DartifactId=protoc -Dversion=2.5.0 -Dclassifier=linux-aarch_64 -Dpackaging=exe -Dfile=/opt/protobuf-2.5.0/bin/protoc

RUN mkdir -p ~/hive-results/

#ARG prebuild=false
#RUN if [ "$prebuild" = "true" ]; then git clone https://github.com/apache/hive \
#    && cd hive \
#    && curl -sL https://patch-diff.githubusercontent.com/raw/liusheng/hive/pull/5.patch | git apply  --index \
#    && mvn clean install -e -B -Pdist -Dtar -DskipTests -Dmaven.javadoc.skip 2>&1 | sudo tee ~/hive-results/hive_build.log \
#    && export PATH=${PATH}:$(realpath ~/hive/hive-dist/target/hive-*-SNAPSHOT/bin); fi

#CMD if [ ! -d hive ]; then git clone https://github.com/apache/hive; fi \
#    && cd hive \
#    && curl -sL https://patch-diff.githubusercontent.com/raw/liusheng/hive/pull/5.patch | git apply  --index \
#    && mvn clean install -e -B -Pdist -Dtar -DskipTests -Dmaven.javadoc.skip 2>&1 | sudo tee ~/hive-results/hive_build.log \
#    && export PATH=$PATH:$(realpath hive-dist/target/hive-*-SNAPSHOT/bin/) \
#    && mvn test -B -e -fn | sudo tee ~/hive-results/hive_all_test.log
