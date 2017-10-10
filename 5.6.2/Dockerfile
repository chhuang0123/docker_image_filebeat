FROM ubuntu:16.04

LABEL maintainer "chhuang@gmail.com"

ENV FILEBEAT_VERSION=5.6.2 \
    FILEBEAT_SHA512=d518bc69577f37a8d85d9523c275b10d6e11e8d879f847f900f195a44ffdad8417ccbe6c3bd1bbad04f5f6223d8a5420e14b3cd02d77c139c36792829de827d3

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
