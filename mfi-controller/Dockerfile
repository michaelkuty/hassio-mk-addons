FROM mvertes/alpine-mongo

ENV MFI_VERSION=2.1.11

RUN apk --update add openjdk7-jre
RUN apk --update add unzip

ADD https://www.ubnt.com/downloads/mfi/$MFI_VERSION/mFi.unix.zip /

RUN unzip mFi.unix.zip && rm mFi.unix.zip

RUN mkdir -p /mFi/logs && ln -s /dev/stderr /mFi/logs/mongod.log && ln -s /dev/stderr /mFi/logs/server.log

EXPOSE 6843 6080 6081 6880 6443

VOLUME ["/mFi/data"]

WORKDIR /mFi

CMD ["java", "-jar", "/mFi/lib/ace.jar", "start"]