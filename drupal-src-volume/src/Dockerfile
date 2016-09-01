# from https://www.drupal.org/requirements/php#drupalversions
FROM debian:jessie

# https://www.drupal.org/node/3060/release
ENV DRUPAL_VERSION 8.1.8
ENV DRUPAL_MD5 7c00b318590a22f2df7a18cf70df06dc

RUN apt-get update && apt-get install -y curl \
    && curl -sfSL "http://ftp.drupal.org/files/projects/drupal-${DRUPAL_VERSION}.tar.gz" -o drupal.tar.gz \
    && echo "${DRUPAL_MD5} *drupal.tar.gz" | md5sum -c - \
    && apt-get purge -y curl \
    && apt-get autoremove -y \
    && mkdir -p /var/www/html

CMD cd /var/www/html; tar -xz --strip-components=1 -f /drupal.tar.gz; rm /drupal.tar.gz; chown -R www-data:www-data sites modules themes; echo 'Drupal files unpacked'

VOLUME /var/www/html
