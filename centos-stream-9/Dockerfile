FROM quay.io/centos/centos:stream9

# Configurar el entorno básico
RUN dnf clean all && \
    dnf update -y && \
    dnf install -y yum-utils && \
    dnf clean all

# Definir el shell predeterminado
CMD ["/bin/bash"]
