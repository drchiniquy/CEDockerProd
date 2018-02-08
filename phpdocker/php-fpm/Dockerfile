FROM php:5.6-fpm

RUN apt-get update

RUN apt-get install -y wget unzip git gcc pkg-config libcurl4-openssl-dev libssl-dev openssl

RUN git clone -b 2.0.x https://github.com/phalcon/cphalcon.git cphalcon-2.0.x && \
    cd cphalcon-2.0.x/build/ && \
    ./install

RUN docker-php-ext-enable phalcon.so

RUN pear install XML_Parser

RUN echo "date.timezone=\"America/New_York\"" > /usr/local/etc/php/conf.d/timezone.ini

RUN apt-get update && \
    apt-get install -y libmemcached-dev \
                       zlib1g-dev \
                       freetds-bin \
                       freetds-dev \
                       freetds-common \
                       libct4 \
                       libsybdb5 \
                       tdsodbc \
                       libfreetype6-dev \
                       libjpeg62-turbo-dev \
                       libmcrypt-dev \
                       libpng12-dev \
                       libldap2-dev \
                       zlib1g-dev \
                       libc-client-dev && \
	pecl install memcached-2.2.0 apcu-4.0.10 mongo xdebug && \
	docker-php-ext-enable memcached mongo

RUN docker-php-ext-install pdo pdo_mysql

RUN pecl install memcache
RUN docker-php-ext-enable memcache apcu mongo

RUN pecl install xdebug-2.5.3
# Copy custom configuration
#COPY xdebug.ini /usr/local/etc/php/conf.d/
RUN docker-php-ext-enable xdebug

#FROM phpdockerio/php56-fpm:latest
#WORKDIR "/application"
#
## Install selected extensions and other stuff
#RUN apt-get update \
#    && apt-get upgrade -y \
#    && apt-get install -y software-properties-common \
#    && apt-get -y --no-install-recommends install  php5-memcached php5-mongo php5-mysql php5-dbg php5-adodb php5-geoip php5-pecl-http php5-imagick php5-memcache php5-phpdbg php5-xdebug php5-xsl php5-json \
#    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
#
#RUN apt-get update
#
#RUN apt-get install -y wget unzip git gcc php5-dev
#
#RUN git clone -b 2.0.x https://github.com/phalcon/cphalcon.git cphalcon-2.0.x && \
#    cd cphalcon-2.0.x/build/ && \
#    ./install
#
#RUN docker-php-ext-enable phalcon.so


# Install phalcon
#RUN apt-add-repository -y ppa:phalcon/legacy \
#    && apt-get update \
#    && apt-get install php5-dev libpcre3-dev gcc make \
#    && git clone --depth 1 https://github.com/phalcon/cphalcon.git \
#    && cd cphalcon \
#    && git remote set-branches origin '2.0.x' \
#    && git fetch --depth 1 origin 2.0.x \
#    && git checkout 2.0.x \
#    && cd build \
#    && ./install

#RUN apt-get update && apt-get install --no-install-recommends -y \
#        wget \
#        vim \
#        git \
#        unzip
#
## Install PHP extensions deps
#RUN apt-get update \
#    && apt-get install --no-install-recommends -y \
#        libfreetype6-dev \
#        libjpeg62-turbo-dev \
#        libmcrypt-dev \
#        libpng12-dev \
#        zlib1g-dev \
#        libicu-dev \
#        g++ \
#        unixodbc-dev \
#        libxml2-dev \
#        libaio-dev \
#        libgearman-dev \
#        libmemcached-dev \
#        freetds-dev \
#	libssl-dev \
#	openssl
#
## Install Composer
#RUN curl -sS https://getcomposer.org/installer | php -- \
#        --install-dir=/usr/local/bin \
#        --filename=composer
#
## Install PHP extensions
#RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
#    && echo 'instantclient,/opt/oracle/instantclient_12_1/' | pecl install oci8-2.0.10 \
#    && docker-php-ext-configure pdo_oci --with-pdo-oci=instantclient,/opt/oracle/instantclient_12_1,12.1 \
#    && docker-php-ext-configure pdo_dblib --with-libdir=/lib/x86_64-linux-gnu \
#    && pecl install apcu-4.0.10 \
#    && pecl install redis-2.2.8 \
#    && pecl install gearman \
#    && pecl install memcached-2.2.0 \
#    && docker-php-ext-install \
#            iconv \
#            mbstring \
#            intl \
#            mcrypt \
#            gd \
#            pgsql \
#            mysqli \
#            pdo_pgsql \
#            pdo_mysql \
#            pdo_oci \
#            pdo_dblib \
#            soap \
#            sockets \
#            zip \
#            pcntl \
#            ftp \
#    && docker-php-ext-enable \
#            oci8 \
#            apcu \
#            memcached \
#            redis \
#            gearman \
#            opcache

#RUN curl -s https://packagecloud.io/install/repositories/phalcon/stable/script.deb.sh | bash \
#    && apt-add-repository -y ppa:phalcon/legacy \
##    && apt-get install -y ppa:phalcon/legacy \
#    && apt-get install -y php5-phalcon \
#    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
