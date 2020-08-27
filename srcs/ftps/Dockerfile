FROM alpine:3.11.3

RUN apk update
RUN apk add musl busybox
RUN apk add bash pure-ftpd --repository http://dl-3.alpinelinux.org/alpine/edge/testing/ --allow-untrusted --no-cache
RUN mkdir -p /home/ftp/admin /var/lib/ftp/ /usr/local/etc/
RUN touch /usr/local/etc/pureftpd.passwd /etc/pureftpd.passwd

RUN addgroup ftpgroup && adduser -g ftpgroup -s /sbin/nologin -D ftpuser
RUN mkdir -p /home/ftp \
	&& chown ftpuser:ftpgroup /home/ftp \
	&& chmod -w /home/ftp

RUN adduser admin -g ftpgroup --disabled-password && echo "admin:admin" | chpasswd
RUN chown admin /home/admin

COPY pure-ftpd.pem /etc/ssl/private/
COPY entrypoint.sh /entrypoint.sh

EXPOSE 21 20 30020-30023
CMD ["sh", "/entrypoint.sh"]
