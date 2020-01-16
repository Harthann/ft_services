FROM alpine:3.11.2

MAINTAINER nieyraud

#############################
# INSTALLING DEPENDENCIES	#
#############################

RUN apk -f upgrade	&& \
	apk -f update	&& \
	apk add -f php-fpm openrc wget && \
	apk add -f vim && \
	wget https://files.phpmyadmin.net/phpMyAdmin/4.9.4/phpMyAdmin-4.9.4-all-languages.tar.gz && \
	tar -xvf phpMyAdmin-4.9.4-all-languages.tar.gz && rm phpMyAdmin-4.9.4-all-languages.tar.gz && \
	mv phpMyAdmin-4.9.4-all-languages phpmyadmin

#############################
#	ADDING PRECONFIG FILES	#
#############################


#############################
#	CLEANING CONTAINER		#
#############################


#############################
#	LAUNCHING COMMAND		#
#############################

CMD sh