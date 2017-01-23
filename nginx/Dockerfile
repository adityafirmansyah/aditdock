# Set the base image to Alpine
FROM alpine:edge

# File Author / Maintainer
MAINTAINER Aditya Firmansyah <adit@incuvius.com>

ARG PHP_UPSTREAM=php-fpm

# Install nginx
RUN apk --update add nginx \
    && rm -rf /var/cache/apk/* \
    && adduser -D -S -h /var/cache/nginx -s /sbin/nologin -G www-data www-data \
    && chown -R www-data:www-data /var/lib/nginx \
    && rm /etc/nginx/conf.d/default.conf \
    && echo "upstream php { server ${PHP_UPSTREAM}:9000; }" > /etc/nginx/conf.d/upstream.conf \
    && cat /etc/nginx/conf.d/upstream.conf

ADD nginx.conf /etc/nginx/

# Expose the ports for nginx
EXPOSE 80 443

CMD ["nginx"]
