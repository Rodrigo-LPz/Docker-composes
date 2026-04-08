FROM php:8.4-fpm

# Dependencias para LDAP
RUN apt-get update \
  && apt-get install -y libldap2-dev libsasl2-dev libssl-dev \
  && rm -rf /var/lib/apt/lists/*

# Instalar extensiones necesarias para MySQL
#RUN docker-php-ext-install mysqli pdo pdo_mysql
# Instalar extensiones necesarias para MySQL + LDAP
RUN docker-php-ext-configure ldap \
  && docker-php-ext-install ldap mysqli pdo pdo_mysql

# Configurar memoria (opcional, ya está en compose.yaml)
RUN echo "memory_limit = 256M" >> /usr/local/etc/php/conf.d/memory.ini

WORKDIR /var/www/html

EXPOSE 9000