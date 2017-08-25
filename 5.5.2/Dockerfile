FROM ubuntu:16.04

LABEL maintainer "chhuang@gmail.com"

ENV FILEBEAT_VERSION=5.5.2 \
    FILEBEAT_SHA1=4191e8864b1d074f6c2a303f22cc2ed0c6361ee5

ADD https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz /tmp/

COPY entrypoint.sh filebeat.yml /
COPY conf.d /conf.d/

RUN set -x && \
    cd /tmp && \
    echo "${FILEBEAT_SHA1}  filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz" | sha1sum -c - && \
    tar xzvf "filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz" && \
    cp "filebeat-${FILEBEAT_VERSION}-linux-x86_64/filebeat" /bin && \
    rm -rf filebeat* && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENTRYPOINT ["/entrypoint.sh"]
CMD [ "filebeat", "-e" ]
