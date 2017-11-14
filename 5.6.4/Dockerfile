FROM ubuntu:16.04

LABEL maintainer "chhuang@gmail.com"

ENV FILEBEAT_VERSION=5.6.4 \
    FILEBEAT_SHA512=4c185861bde169a9109a33dbb97b0f75421e30480ee5373c5a04c1e95da8c9243e085806ec04df7eee9ca8f084cf67015840ad824e2a111f6fbace624324c634

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
