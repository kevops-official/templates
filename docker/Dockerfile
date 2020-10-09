FROM nginx

COPY web.conf /etc/nginx/conf.d/

COPY src /var/www/html

RUN rm -f /etc/nginx/conf.d/default.conf