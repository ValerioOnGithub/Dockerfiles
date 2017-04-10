FROM centos:centos7

RUN yum -y update
RUN yum -y upgrade
RUN yum -y install wget
RUN wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN wget http://rpms.remirepo.net/enterprise/remi-release-7.rpm
RUN rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
RUN yum -y install yum-utils
RUN yum-config-manager --enable remi-php71
RUN yum install -y \
		php \
		php-cli \
		php-bcmath \
		php-gd \
		php-mbstring \
		php-mysqlnd \
		php-opcache \
		php-pecl-geoip \
		php-devel \
		mod_ssl \
		php-mcrypt \
		php-xml \
		php-gettext \
		php-intl \
		php-pecl-igbinary \
		php-soap \
		php-redis \
		php-fpm \
		composer
RUN yum clean all
COPY ./configs/www.conf /etc/php-fpm.d/www.conf

VOLUME /var/www

EXPOSE 9000
CMD ["php-fpm", "--nodaemonize"]
