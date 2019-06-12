FROM php:7.1.3-fpm
ENV PHP_INI_DIR /usr/local/etc/php/
COPY customized.ini $PHP_INI_DIR/conf.d/customized.ini
COPY opcache.ini $PHP_INI_DIR/conf.d/opcache.ini

# run for workaround Issue with fetching http://deb.debian.org/debian/dists/jessie-updates/InRelease with docker
RUN printf "deb http://archive.debian.org/debian/ jessie main\ndeb-src http://archive.debian.org/debian/ jessie main\ndeb http://security.debian.org jessie/updates main\ndeb-src http://security.debian.org jessie/updates main" > /etc/apt/sources.list

# php extension
RUN apt-get update -y && apt-get install -y htop cron nano libicu-dev \
    libmcrypt-dev libxml2-dev libxslt-dev libzip-dev libfreetype6-dev \
    libjpeg62-turbo-dev libpng12-dev \
    && docker-php-ext-install -j$(nproc) bcmath calendar \
    exif gettext intl mcrypt mysqli pcntl pdo_mysql soap \
    sockets wddx xsl zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd
