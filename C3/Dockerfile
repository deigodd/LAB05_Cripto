FROM ubuntu:20.10

# Configurar repositorios old-releases para versión EOL
RUN sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com\|ports.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list && \
    sed -i 's/ubuntu-ports/ubuntu/g' /etc/apt/sources.list

# Actualizar e instalar solo cliente SSH
RUN apt-get update && apt-get install -y \
    openssh-client \
    iputils-ping \
    net-tools \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /root
CMD ["/bin/bash", "-c", "tail -f /dev/null"]