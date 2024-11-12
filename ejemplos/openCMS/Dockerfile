# Usar la imagen base de OpenJDK y Tomcat
FROM tomcat:9-jdk11

# Actualizar el sistema e instalar curl y unzip
RUN apt-get update && apt-get install -y curl unzip

# Establecer el directorio de trabajo
WORKDIR /usr/local/tomcat

# Descargar OpenCMS 17.0 desde la URL proporcionada
RUN curl -L -o opencms-17.0.zip http://www.opencms.org/downloads/opencms/opencms-17.0.zip

# Descomprimir el archivo zip
RUN unzip opencms-17.0.zip -d webapps/

# Exponer el puerto 8080
EXPOSE 8080

# Iniciar Tomcat
CMD ["catalina.sh", "run"]
