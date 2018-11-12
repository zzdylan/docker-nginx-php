FROM centos:latest
RUN yum -y install wget \
#下载编译安装php7.1
&& mkdir -p /downloads \
&& cd /downloads \
&& wget http://cn.php.net/distributions/php-7.1.24.tar.gz \
&& tar xzf /downloads/php-7.1.24.tar.gz \
&& cd /downloads/php-7.1.24 \
&& yum  -y  install  gcc  gcc-c++ libxml2-devel m4 autoconf pcre-devel make cmake bison \
&& ./configure --prefix=/usr/local/php --with-config-file-path=/usr/local/php/etc  --enable-fpm \
&& make && make install \
&& cp /downloads/php-7.1.24/php.ini-development /usr/local/php/etc/php.ini \
&& cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf \
&& cp /usr/local/php/etc/php-fpm.d/www.conf.default /usr/local/php/etc/php-fpm.d/www.conf \
&& mkdir -p /web 
COPY ./config/www.conf /usr/local/php/etc/php-fpm.d/
COPY ./config/php-fpm.conf /usr/local/php/etc/
CMD /usr/local/php/sbin/php-fpm