FROM tu6ge/nginx-php

RUN echo http://mirrors.ustc.edu.cn/alpine/v3.7/main/  > /etc/apk/repositories \
	&& echo http://mirrors.ustc.edu.cn/alpine/v3.7/community/  >> /etc/apk/repositories \
	&& apk update \
	&& apk upgrade \
	&& apk add hiredis-dev libmcrypt-dev gmp-dev icu-dev linux-headers musl --virtual .phpize-deps autoconf m4 make g++ gcc \
    && pecl download swoole-4.0.2 \
	&& mkdir -p /tmp/swoole \
    && tar -xf swoole-4.0.2.tgz  -C /tmp/swoole --strip-components=1 \
    && rm -f swoole-4.0.2.tgz \
	&& docker-php-ext-install sockets \
	&& docker-php-ext-configure /tmp/swoole/ --enable-async-redis --enable-openssl --enable-mysqlnd --enable-sockets=/usr/local/include/php/ext/sockets \
    && docker-php-ext-install /tmp/swoole \
	&& docker-php-ext-install intl

EXPOSE 443 80 9000

CMD ["/start.sh"]