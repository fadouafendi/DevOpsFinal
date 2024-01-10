FROM		nginx		
MAINTAINER	brahim.hamdi.consult@gmail.com
COPY            wiki.conf      /etc/nginx/conf.d/default.conf
# COPY		services.sh	/
# RUN		chmod +x /services.sh
RUN		apt update -y && apt install -y mariadb-client nano php-mbstring gzip unzip php-fpm php-xml php-mysql
RUN		usermod -a -G www-data nginx
ADD		https://releases.wikimedia.org/mediawiki/1.32/mediawiki-1.32.1.tar.gz /
RUN		tar xzvf /mediawiki-1.32.1.tar.gz && mv /mediawiki-1.32.1 /usr/share/nginx/wiki && chown -R www-data.www-data /usr/share/nginx/wiki
VOLUME		/var/log/nginx /usr/share/nginx /etc/nginx/conf.d/
# ENTRYPOINT	/bin/sh -c /services.sh
CMD		service	php7.3-fpm start && nginx -g "daemon off;"
