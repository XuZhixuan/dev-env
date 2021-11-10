FROM ubuntu

LABEL maintainer="sxxuzhixuan@hotmail.com"

RUN sed -i 's/archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list
RUN sed -i 's/security.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list
RUN sed -i 's/ports.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list

RUN apt-get update && apt-get install -y ca-certificates

COPY ./etc /etc

RUN apt-get update && apt-get install -y \
    php8.0 \
    php8.0-fpm \
    php8.0-zip \
    php8.0-xml \
    php8.0-mysql \
    php8.0-mbstring \
    php8.0-curl

COPY ./usr /usr

RUN composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
