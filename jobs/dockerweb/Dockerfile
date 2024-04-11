# Base image with PHP 7.1.17 and Apache
FROM php:7.1.17-apache

# Set maintainer label
LABEL maintainer="Jaivic"

# Enable mod_rewrite
RUN a2enmod rewrite

# Install required dependencies (replace with your actual needs)
RUN apt-get install -y zlib1g-dev libicu-dev libxml2-dev libpq-dev

# Install and configure PHP extensions
RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
  && docker-php-ext-install pdo pdo_mysql pdo_pgsql zip intl xmlrpc soap opcache \
  && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd

# Install vim (optional)
RUN apt-get install vim -y

# Copy your application code (exclude unnecessary files)
COPY . /var/www/html/ --from=source .gitignore

# Working directory for your application
WORKDIR /var/www/html/
