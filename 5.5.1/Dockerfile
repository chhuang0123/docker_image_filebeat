FROM ubuntu:16.04

MAINTAINER chhuang <chhuang@gmail.com>

ENV FILEBEAT_VERSION=5.5.1 \
    FILEBEAT_SHA1=2a348d116d5225327af0a9a54702889366af971e

COPY entrypoint.sh filebeat.yml /
COPY conf.d /conf.d

RUN set -x && \
    apt-get update && \
    apt-get install -y wget && \
    wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz -O /tmp/filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz && \
    cd /tmp && \
    echo "${FILEBEAT_SHA1}  filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz" | sha1sum -c - && \
    tar xzvf "filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz" && \
    cp "filebeat-${FILEBEAT_VERSION}-linux-x86_64/filebeat" /bin && \
    rm -rf filebeat* && \
    apt-get purge -y wget && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENTRYPOINT ["/entrypoint.sh"]
CMD [ "filebeat", "-e" ]

