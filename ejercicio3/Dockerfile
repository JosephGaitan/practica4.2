# Partimos de la imagen base de Debian
FROM debian:12

# Evitamos que la instalación de paquetes nos pida confirmaciones interactivas
ENV DEBIAN_FRONTEND=noninteractive

# Actualizamos repositorios e instalamos Apache, PHP, los módulos necesarios y las herramientas
RUN apt-get update && apt-get install -y \
    apache2 \
    php \
    libapache2-mod-php \
    vim \
    nano \
    net-tools \
    && rm -rf /var/lib/apt/lists/*

# Habilitamos el módulo SSL en Apache
RUN a2enmod ssl

# Creamos los directorios para los certificados (igual que en el Ejercicio 2)
RUN mkdir -p /etc/ssl/certs /etc/ssl/private

# Copiamos la web, los certificados y el VirtualHost
COPY web1 /var/www/html/web1
COPY tls/certs/ca_web1.crt /etc/ssl/certs/
COPY tls/private/ca_web1.key /etc/ssl/private/
COPY web1.com.conf /etc/apache2/sites-available/

# Deshabilitamos el sitio por defecto y habilitamos el nuestro
RUN a2dissite 000-default.conf && a2ensite web1.com.conf

# Exponemos los puertos
EXPOSE 80 443

# Comando para arrancar el servicio de Apache en primer plano y mantener el contenedor vivo
CMD ["apache2ctl", "-D", "FOREGROUND"]