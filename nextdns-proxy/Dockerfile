# Base image
FROM debian:latest

# Portmappings
EXPOSE 53
EXPOSE 53/udp

# Depends
RUN apt-get update && apt-get install -yqq apt-transport-https gnupg gpgv wget locales && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
ENV LANG en_US.utf8

# NextDNS repository
RUN wget -qO - https://nextdns.io/repo.gpg | apt-key add - && echo "deb https://nextdns.io/repo/deb stable main" | tee /etc/apt/sources.list.d/nextdns.list && apt-get update && apt-get install nextdns -yqq && rm -rf /var/lib/apt/lists/*

# Copy scripts and make them executable
WORKDIR /var/nextdns
ADD run.sh /var/nextdns
RUN chmod guo+x run.sh && ./var/nextdns/run.sh

# Run
ENTRYPOINT /var/nextdns/run.sh