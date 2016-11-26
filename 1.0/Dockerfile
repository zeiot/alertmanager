# VERSION 0.5.0
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    zeiot/rpi-alertmanager

FROM resin/armv7hf-debian:jessie
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV ALERTMANAGER_VERSION 0.5.0

ADD https://github.com/prometheus/alertmanager/releases/download/v${ALERTMANAGER_VERSION}/alertmanager-${ALERTMANAGER_VERSION}.linux-armv7.tar.gz /alertmanager.tar.gz

RUN tar -xf /alertmanager.tar.gz && \
    rm /alertmanager.tar.gz && \
    mv alertmanager-${ALERTMANAGER_VERSION}.linux-armv7 /usr/share/alertmanager && \
    cp /usr/share/alertmanager/alertmanager /usr/bin/alertmanager && \
    mkdir /etc/alertmanager && \
    cp /usr/share/alertmanager/simple.yml /etc/alertmanager/simple.yml

EXPOSE     9093

VOLUME     [ "/alertmanager" ]

ENTRYPOINT [ "/usr/bin/alertmanager" ]

CMD        [ "-config.file=/etc/alertmanager/simple.yml", \
             "-storage.path=/alertmanager" ]
