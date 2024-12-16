#Obtenemos la imagen de ubuntu apache
FROM ubuntu:latest

LABEL autors="Egoitz Larrea" version="1.0" description="Ubuntu+proftp" creationDate="08-12-2024"

#Actualizamos los paquetes e instalamos ssl
RUN apt-get update
#Instalamos nano

RUN apt-get install nano

#Instalamos ftp
RUN apt-get install -y proftpd


#creamos la estructura de carpeta y copiamos el contenido
RUN mkdir -p ["/srv/ftp/Recursos Contenedor 1"
COPY ["./Recursos Contenedor 1", "/srv/ftp/Recursos Contenedor 1"]
COPY ["proftpd_contenedor1.conf", "/etc/proftpd/proftpd.conf"]
	
EXPOSE  21 50000-50030
