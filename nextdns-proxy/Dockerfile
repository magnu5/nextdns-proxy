#!/bin/bash
FROM debian:latest

EXPOSE 53
EXPOSE 53/udp

RUN apt-get update && apt-get install -y locales && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
ENV LANG en_US.utf8
RUN apt-get install -fy apt-transport-https gnupg gpgv wget
RUN wget -qO - https://nextdns.io/repo.gpg | apt-key add -
RUN echo "deb https://nextdns.io/repo/deb stable main" | tee /etc/apt/sources.list.d/nextdns.list
RUN apt-get update
RUN apt-get remove dnsmasq
RUN apt-get dist-upgrade -y
RUN apt-get autoremove -y
RUN apt-get install -y nextdns

RUN rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/nextdns
COPY run.sh /var/nextdns/run.sh
RUN chmod guo+x /var/nextdns/run.sh

CMD ["/var/nextdns/run.sh"]
