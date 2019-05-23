FROM openjdk:8

LABEL maintainer="Yago Lima <yagotoledolima@gmail.com"

WORKDIR /opt

ARG ANT_VERSION=1.10.5

RUN wget http://ftp.unicamp.br/pub/apache//ant/binaries/apache-ant-$ANT_VERSION-bin.zip && \
    wget https://www.apache.org/dist/ant/binaries/apache-ant-$ANT_VERSION-bin.zip.sha512 && \
    echo -n "`cat apache-ant-$ANT_VERSION-bin.zip.sha512`  apache-ant-$ANT_VERSION-bin.zip" | sha512sum -c && \
    unzip apache-ant-$ANT_VERSION-bin.zip && \
    mv apache-ant-$ANT_VERSION apache-ant

WORKDIR /opt/apache-ant

ENV ANT_HOME /opt/apache-ant
ENV PATH="$PATH:/opt/apache-ant/bin"

ENTRYPOINT ["ant"]
