FROM alpine:3.5

MAINTAINER Open Source Services [opensourceservices.fr]

RUN apk add --update \
    transmission-daemon \
    && rm -rf /var/cache/apk/*

RUN mkdir -p /etc/transmission-daemon
# tranmission uid hack
RUN deluser transmission && adduser -u 5000 -s /sbin/nologin -H -D transmission transmission

COPY src/ .

VOLUME ["/downloads", "/etc/transmission-daemon"]

EXPOSE 9091 51413/tcp 51413/udp

#ENV USERNAME admin
#ENV PASSWORD password

RUN chmod +x /start-transmission.sh
CMD ["/start-transmission.sh"]
