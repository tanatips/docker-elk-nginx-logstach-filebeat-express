FROM php:7.2-apache

# Update and install packages
RUN apt-get update && \
    apt-get install -y git && \
    rm -rf /var/lib/apt/lists/*

# Clone DVWA from GitHub
RUN git clone https://github.com/ethicalhack3r/DVWA /var/www/html/dvwa

# Set DVWA configuration
RUN cp /var/www/html/dvwa/config/config.inc.php.dist /var/www/html/dvwa/config/config.inc.php && \
    sed -i 's/^\(.*\)db_user\(.*\)$/\\1root\\2/' /var/www/html/dvwa/config/config.inc.php && \
    sed -i 's/^\(.*\)db_password\(.*\)$/\\1password\\2/' /var/www/html/dvwa/config/config.inc.php && \
    sed -i 's/^\(.*\)db_database\(.*\)$/\\1dvwa\\2/' /var/www/html/dvwa/config/config.inc.php

# Set permissions
RUN chown -R www-data:www-data /var/www/html/dvwa && \
    chmod -R 755 /var/www/html/dvwa

# Set environment variables
ENV MYSQL_HOST=db \
    MYSQL_USER=root \
    MYSQL_PASSWORD=password \
    MYSQL_DATABASE=dvwa

# Enable Apache2 modules
RUN a2enmod rewrite
