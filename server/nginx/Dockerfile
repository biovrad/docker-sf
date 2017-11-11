FROM nginx:1.13

MAINTAINER Oleh Hrebeniuk <olehhrebeniuk@gmail.com>

RUN apt-get update && apt-get install -y \
    supervisor

ADD supervisord.conf /etc/
ADD nginx.conf /etc/nginx/nginx.conf

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

EXPOSE 80 443

# Executing supervisord
CMD ["supervisord", "-n"]