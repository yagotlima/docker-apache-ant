FROM alpine:3.9 as ant-download

WORKDIR /ant

ARG ANT_VERSION=1.10.5

RUN wget http://ftp.unicamp.br/pub/apache//ant/binaries/apache-ant-$ANT_VERSION-bin.zip && \
    wget https://www.apache.org/dist/ant/binaries/apache-ant-$ANT_VERSION-bin.zip.sha512 && \
    echo -n "`cat apache-ant-$ANT_VERSION-bin.zip.sha512`  apache-ant-$ANT_VERSION-bin.zip" | sha512sum -c && \
    unzip apache-ant-$ANT_VERSION-bin.zip && \
    mv apache-ant-$ANT_VERSION apache-ant

FROM openjdk:8-alpine

LABEL maintainer="Yago Lima <yagotoledolima@gmail.com"

WORKDIR /opt/apache-ant

COPY --from=ant-download /ant/apache-ant ./

ENV ANT_HOME /opt/apache-ant
ENV PATH="$PATH:/opt/apache-ant/bin"

ENTRYPOINT ["ant"]
