FROM debian:latest

RUN apt-get update -y && apt-get upgrade -y \
    && apt-get install -y apache2

WORKDIR /etc/apache2/sites-available/
COPY *.conf .
RUN rm 000-default.conf \
    && a2ensite dms.conf gitea.conf vaultwarden.conf \
    && a2enmod ssl rewrite proxy proxy_http headers

EXPOSE 80 443
CMD ["apache2ctl", "-DFOREGROUND"]
