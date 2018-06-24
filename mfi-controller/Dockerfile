ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

ENV MFI_VERSION=2.1.11

RUN apk add --no-cache openjdk7-jre
RUN apk add --no-cache mongodb
RUN apk add --no-cache unzip

ADD https://www.ubnt.com/downloads/mfi/$MFI_VERSION/mFi.unix.zip /

RUN unzip mFi.unix.zip && rm mFi.unix.zip

RUN mkdir -p /mFi/logs && ln -s /dev/stderr /mFi/logs/mongod.log && ln -s /dev/stderr /mFi/logs/server.log

EXPOSE 6843/tcp 6080/tcp 6880/tcp 6443/tcp 2323/tcp
EXPOSE 10001/udp 3478/udp 1900/udp

VOLUME ["/mFi/data"]

WORKDIR /mFi

CMD [ "/run.sh" ]
