# Ejercicio 2: Apache + PHP

## Instrucciones para construir y ejecutar

1. **Construir la imagen:**
   Ejecuta el siguiente comando en el directorio donde se encuentra el Dockerfile:
   `docker build -t joseph/apache-php-daw2 .`

2. **Ejecutar el contenedor:**
   Arranca el contenedor mapeando los puertos 80 y 443 para habilitar HTTP y HTTPS:
   `docker run -d --name mi-web-apache -p 80:80 -p 443:443 joseph/apache-php-daw2`

3. **Acceso:**
   - HTTP: `http://localhost`
   - HTTPS: `https://localhost` (Acepta la advertencia de seguridad del certificado autofirmado).

   REPO DE GITHUB https://github.com/JosephGaitan/practica4.2