FROM nginx:1.14-alpine

ADD nginx.conf /etc/nginx/
ADD local.conf /etc/nginx/conf.d/local.conf

RUN adduser -D -H -u 1000 -s /bin/bash www-data && \
    rm /etc/nginx/conf.d/default.conf

CMD ["nginx"]

EXPOSE 80 443