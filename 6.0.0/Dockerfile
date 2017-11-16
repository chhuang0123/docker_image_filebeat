FROM ubuntu:16.04

LABEL maintainer "chhuang@gmail.com"

ENV FILEBEAT_VERSION=6.0.0 \
    FILEBEAT_SHA512=2bd64f9f683bd1f3551637f34333da919cf5c9628a20dea76d1c4df9679b26d5bc234802ff03fb7a418681bed7081bf859ec7a2bc9c0a54bd501af8c0fa9f850

ADD https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz /tmp/

COPY entrypoint.sh filebeat.yml /
COPY conf.d /conf.d/

RUN set -x && \
    cd /tmp && \
    echo "${FILEBEAT_SHA512}  filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz" | sha512sum -c - && \
    tar xzvf "filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz" && \
    cp "filebeat-${FILEBEAT_VERSION}-linux-x86_64/filebeat" /bin && \
    rm -rf filebeat* && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENTRYPOINT ["/entrypoint.sh"]
CMD [ "filebeat", "-e" ]
