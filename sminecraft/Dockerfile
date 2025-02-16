# Usar la imagen base de Debian 12
FROM debian:12

# Copiar el directorio completo minecraft-terror a la raíz del contenedor
COPY minecraft-terror /minecraft-terror

# Establecer el directorio de trabajo
WORKDIR /minecraft-terror

# Actualizar paquetes e instalar el .deb de OpenJDK
RUN apt update && \
    apt install -y ./openlogic-openjdk-jre-21.0.5+11-linux-x64-deb.deb && \
    rm -f openlogic-openjdk-jre-21.0.5+11-linux-x64-deb.deb

# Asegurarse de que go.sh sea ejecutable
RUN chmod +x go.sh

# Exponer el puerto predeterminado de Minecraft
EXPOSE 25565

# Comando para ejecutar el script go.sh
CMD ["bash", "./go.sh"]
