FROM ubuntu:16.04

RUN apt-get update && \
    apt-get install -y nginx && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN apt-get install nginx    
COPY nginx.conf /etc/nginx/
COPY app.conf /etc/nginx/sites-available/
COPY ics.conf /etc/nginx/sites-available/
COPY padmin.conf /etc/nginx/sites-available/
COPY b2c.conf /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/ics.conf /etc/nginx/sites-enabled/ics
RUN ln -s /etc/nginx/sites-available/app.conf /etc/nginx/sites-enabled/app
RUN ln -s /etc/nginx/sites-available/b2c.conf /etc/nginx/sites-enabled/b2c
RUN ln -s /etc/nginx/sites-available/padmin.conf /etc/nginx/sites-enabled/padmin
RUN rm /etc/nginx/sites-enabled/default

RUN echo "upstream php-upstream { server php-fpm:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
