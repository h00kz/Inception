FROM debian:buster

RUN apt update -y && apt upgrade -y && apt-get install nginx -y && apt-get install openssl -y

RUN mkdir -p /etc/ssl/private/
RUN mkdir -p /etc/ssl/certs/
COPY ./conf/nginx.conf /etc/nginx/conf.d/
COPY ./files/index.html /var/www/html/
RUN openssl req -x509 -nodes -days 365 -newkey rsa:4096 \ 
         -keyout /etc/ssl/private/jlarrieu.key \ 
         -out /etc/ssl/certs/jlarrieu.crt \ 
         -sha256 -subj "/C=FR/ST=FRANCE/L=ANGOULEME/O=42 ANGOULEME/OU=jlarrieu/CN=jlarrieu/"

EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]
