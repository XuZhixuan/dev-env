FROM ubuntu

LABEL maintainer="sxxuzhixuan@hotmail.com"

# Using Tsinghua TUNA mirror to speed up.
RUN sed -i 's/archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list
RUN sed -i 's/security.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list
RUN sed -i 's/ports.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list

# Install ca-certificates to enable https
RUN apt-get update && apt-get install -y ca-certificates

# Copy launchpad gpg keys and sources lists
COPY ./etc/apt /etc/apt

# Install php environments
RUN apt-get update && apt-get install -y \    
    php8.0 \
    php8.0-fpm \
    php8.0-zip \
    php8.0-xml \
    php8.0-mysql \
    php8.0-mbstring \
    php8.0-curl

# Enable Composer by uncomment the next 2 lines.
COPY ./usr /usr 
RUN composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

# Using customized config file for php
COPY ./etc/php /etc/php

STOPSIGNAL SIGQUIT

EXPOSE 9000

WORKDIR /var/www/html
CMD [ "php-fpm8.0" ]