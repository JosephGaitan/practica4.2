# Partimos de la imagen oficial con Apache y PHP
FROM php:apache

# Actualizamos e instalamos vim, nano y net-tools
RUN apt-get update && apt-get install -y \
    vim \
    nano \
    net-tools \
    && rm -rf /var/lib/apt/lists/*

# Habilitamos el módulo SSL en Apache
RUN a2enmod ssl

# Copiamos la web, certificados y el VirtualHost al contenedor
COPY web1 /var/www/html/web1
COPY tls/certs/ca_web1.crt /etc/ssl/certs/
COPY tls/private/ca_web1.key /etc/ssl/private/
COPY web1.com.conf /etc/apache2/sites-available/

# Deshabilitamos el sitio por defecto y habilitamos el nuestro
RUN a2dissite 000-default.conf && a2ensite web1.com.conf