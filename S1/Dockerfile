FROM ubuntu:22.10

RUN sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com\|ports.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list && \
    sed -i 's/ubuntu-ports/ubuntu/g' /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
    openssh-server \
    iputils-ping \
    net-tools \
    tcpdump \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/run/sshd

RUN mkdir -p /captures

RUN useradd -m -s /bin/bash prueba && echo "prueba:prueba" | chpasswd

RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

EXPOSE 22

CMD ["/bin/bash", "-c", "/usr/sbin/sshd -D & tail -f /dev/null"]