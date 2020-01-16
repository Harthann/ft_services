FROM alpine:3.11.2

MAINTAINER nieyraud

#############################
# INSTALLING DEPENDENCIES	#
#############################

RUN apk -f upgrade	&& \
	apk -f update	&& \
	apk add -f nginx php-fpm openrc && \
	apk add -f vim && \
	mkdir /etc/nginx/sites-available && \
	mkdir /var/www/html /run/nginx && \
	touch /run/nginx/nginx.pid

#############################
#	ADDING PRECONFIG FILES	#
#############################

COPY ./nginx_srcs/default /etc/nginx/sites-available/default
COPY ./nginx_srcs/nginx.html /var/www/html/nginx.html
COPY ./nginx_srcs/default.conf /etc/nginx/conf.d/default.conf

#############################
#	CLEANING CONTAINER		#
#############################


#############################
#	LAUNCHING COMMAND		#
#############################

CMD rc-status -s && touch /run/openrc/softlevel && rc-service nginx start && sh