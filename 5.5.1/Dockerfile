FROM ubuntu:16.04

LABEL maintainer "chhuang@gmail.com"

ENV FILEBEAT_VERSION=5.5.1
ADD https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz /opt/

COPY entrypoint.sh filebeat.yml /
COPY conf.d /conf.d/

RUN set -x && \
    cp "/opt/filebeat-${FILEBEAT_VERSION}-linux-x86_64/filebeat" /bin && \
    rm -rf /var/lib/apt/lists/* /opt/* /var/tmp/*

ENTRYPOINT ["/entrypoint.sh"]
CMD [ "filebeat", "-e" ]

