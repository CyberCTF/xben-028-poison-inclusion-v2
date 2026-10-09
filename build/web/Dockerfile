# Upstream's Dockerfile (XBEN-028-24/app/Dockerfile) with these changes:
# - the sources are copied from app/app/ (the vendored benchmark folder sits in app/)
# - the build argument FLAG defaults to this lab's fixed flag, the value upstream's Makefile passes
#   (FLAG{sha256 of "XBEN-028-24"}), since the spec passes no build arguments
FROM php:7.4-apache

WORKDIR /var/www/html

RUN docker-php-ext-install pdo

RUN a2enmod rewrite

COPY app/app/website /var/www/html/

RUN chown -R www-data:www-data /var/www/html

ARG FLAG=FLAG{9ed98c4ebcf85ee4c0c9aad626949981a8a7725ddf507d20b6701b7442bdd294}
RUN echo -n $FLAG > /FLAG.txt

EXPOSE 80

CMD ["apache2-foreground"]
