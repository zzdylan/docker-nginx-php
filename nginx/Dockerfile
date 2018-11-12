FROM centos:latest
RUN yum install -y wget \
#编译安装nginx
&& mkdir -p /downloads \
&& cd /downloads \
&& wget http://nginx.org/download/nginx-1.14.1.tar.gz \
&& tar xzf nginx-1.14.1.tar.gz \
&& cd /downloads/nginx-1.14.1 \
&& yum install -y gcc gcc-c++ zlib zlib-devel openssl openssl-devel prce prce-devel \
&& ./configure --prefix=/usr/local/nginx \
&& make && make install \
&& mkdir -p /web \
&& rm -f /usr/local/nginx/conf/nginx.conf
COPY ./config/nginx.conf /usr/local/nginx/conf/
CMD /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
