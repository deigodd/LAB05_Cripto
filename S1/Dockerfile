FROM ubuntu:22.10

# Configurar repositorios old-releases para versión EOL
RUN sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com\|ports.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list && \
    sed -i 's/ubuntu-ports/ubuntu/g' /etc/apt/sources.list

# Actualizar e instalar servidor SSH
RUN apt-get update && apt-get install -y \
    openssh-server \
    iputils-ping \
    net-tools \
    && rm -rf /var/lib/apt/lists/*

# Configurar SSH Server
RUN mkdir -p /var/run/sshd

# Crear usuario prueba solo en el servidor
RUN useradd -m -s /bin/bash prueba && echo "prueba:prueba" | chpasswd

# Permitir login con password
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Exponer puerto SSH
EXPOSE 22

# Iniciar SSH y mantener contenedor activo
CMD ["/bin/bash", "-c", "/usr/sbin/sshd -D & tail -f /dev/null"]