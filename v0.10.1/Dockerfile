FROM java:8-jre-alpine

MAINTAINER Orange Mi <orangemiwj@gmail.com>

RUN apk add --update unzip wget curl bash && rm -rf /var/cache/apk/*

ENV KAFKA_VERSION="0.10.1.1" SCALA_VERSION="2.11"

RUN mkdir /opt && \
  wget -q "http://mirrors.cnnic.cn/apache/kafka/${KAFKA_VERSION}/kafka_${SCALA_VERSION}-${KAFKA_VERSION}.tgz" -O "/tmp/kafka_${SCALA_VERSION}-${KAFKA_VERSION}.tgz" && \
  tar xfz /tmp/kafka_${SCALA_VERSION}-${KAFKA_VERSION}.tgz -C /opt && \
  rm /tmp/kafka_${SCALA_VERSION}-${KAFKA_VERSION}.tgz

ENV KAFKA_HOME=/opt/kafka_${SCALA_VERSION}-${KAFKA_VERSION}
VOLUME ["/kafka"]

ADD start-kafka.sh /usr/bin/start-kafka.sh
# ADD broker-list.sh /usr/bin/broker-list.sh
# ADD create-topics.sh /usr/bin/create-topics.sh

# Use "exec" form so that it runs as PID 1 (useful for graceful shutdown)
CMD ["/usr/bin/start-kafka.sh"]
