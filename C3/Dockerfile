FROM ubuntu:20.10

RUN sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com\|ports.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list && \
    sed -i 's/ubuntu-ports/ubuntu/g' /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
    openssh-client \
    iputils-ping \
    net-tools \
    tcpdump \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /captures

WORKDIR /root
CMD ["/bin/bash", "-c", "tail -f /dev/null"]