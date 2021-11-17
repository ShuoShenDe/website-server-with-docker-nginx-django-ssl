FROM nginx:1.19.0-alpine

RUN rm /etc/nginx/conf.d/default.conf

WORKDIR /etc/nginx/
RUN mkdir /etc/nginx/socket/

COPY ./default.conf /etc/nginx/conf.d/default.conf
