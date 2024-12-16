	#Obtenemos la imagen de ubuntu apache
FROM ubuntu:latest

LABEL autors="Egoitz Larrea" version="1.0" description="Ubuntu+proftp+tls" creationDate="08-12-2024"

#Actualizamos los paquetes e instalamos ssl
RUN apt-get update && apt-get install openssl

#Instalamos nano
RUN apt-get install nano

#Instalamos ftp
RUN apt-get install -y proftpd && apt-get install  -y  proftpd-mod-crypto

#Generamos el genpkey 
RUN openssl genpkey -algorithm RSA   -out /etc/ssl/private/proftpd.key -pkeyopt rsa_keygen_bits:4096
#Generamos la clave publica 
RUN openssl req -new -key /etc/ssl/private/proftpd.key -x509 -days 365 -out /etc/ssl/certs/proftpd.crt -subj "/C=ES/ST=Bizkaiz/L=Bizkaia/O=Egoitz Larrea Manzano/OU=Birt/CN=www.eglarrea-birt.eus" 

#creamos el usuario
RUN useradd deaw -m -d /srv/deaw  --password "$(openssl passwd -1 "deaw")" --shell /bin/false 

#creamos la estructura de carpeta y copiamos el contenido
RUN mkdir -p ["/srv/deaw/Recursos Contenedor 2"]
COPY ["./Recursos Contenedor 2", "/srv/deaw/Recursos Contenedor 2"]
COPY ["proftpd_contenedor2.conf", "/etc/proftpd/proftpd.conf"]
COPY ["tls.conf", "/etc/proftpd/tls.conf"]
COPY ["modules.conf", "/etc/proftpd/modules.conf"]

EXPOSE  21 50000-50030
