FROM centos:7

LABEL maintainer="Helias Karagozidis"

ARG PHALCON_VERSION=4
ARG PHALCON_EXT_PATH=php7/64bits

# Install Apache
RUN yum -y update
RUN yum -y install httpd httpd-tools

# Install EPEL
RUN yum -y install epel-release
RUN yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm
RUN yum-config-manager --enable remi-php74

# Install Service handle
RUN yum -y install initscripts

# Install Tools
RUN  yum -y install vim unzip git

# Install PHP & phalcon
RUN yum -y install php php-common.x86_64 php-devel.x86_64  php-fpm.x86_64 php-gd.x86_64 \
                    php-intl.x86_64 php-json.x86_64 php-mbstring.x86_64 php-mysqlnd.x86_64 \
                    php-pdo.x86_64 php-pecl-cassandra.x86_64 php-pecl-igbinary.x86_64 php-pecl-mongodb.x86_64 \
                    php-pecl-swoole4.x86_64 php-pgsql.x86_64 php-process.x86_64 php-bcmath.x86_64 \
                    php-xml.x86_64 php-opcache.x86_64 php-pecl-gmagick.x86_64 php-pecl-geoip.x86_64 \
                    php-pecl-memcache.x86_64 php-pecl-memcached.x86_64 php-pecl-mcrypt.x86_64 php-pecl-redis.x86_64 \
                    php-pecl-zip.x86_64 php-phalcon4.x86_64 php-sodium.x86_64 php-wkhtmltox.x86_64 composer.noarch \
                    php-pecl-decimal.x86_64 php-pecl-ds.x86_64 php-pecl-rdkafka.x86_64 php-soap.x86_64

# Install Phalcon composer
# RUN cd /opt
# WORKDIR /opt
# RUN git clone https://github.com/phalcon/phalcon-devtools.git
# WORKDIR /opt/phalcon-devtools
# # RUN cd /opt/phalcon-devtools
# RUN composer install

# Update Apache Configuration
RUN sed -E -i -e '/<Directory "\/var\/www\/html">/,/<\/Directory>/s/AllowOverride None/AllowOverride All/' /etc/httpd/conf/httpd.conf
RUN sed -E -i -e 's/DirectoryIndex (.*)$/DirectoryIndex index.php \1/g' /etc/httpd/conf/httpd.conf

EXPOSE 80

# Start Apache
CMD ["/usr/sbin/httpd","-D","FOREGROUND"]
