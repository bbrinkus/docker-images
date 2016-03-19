FROM alpine:3.3
MAINTAINER Balazs Brinkus <balazs@brinkus.com>
LABEL Description="Alpine Linux with Java 8"

# Environment variables
ENV GLIBC_ROOT_URL https://github.com/andyshinn/alpine-pkg-glibc/releases/download/2.23-r1
ENV GLIBC_FILE glibc-2.23-r1.apk

ENV JDK_ROOT_URL http://download.oracle.com/otn-pub/java/jdk/8u74-b02/jdk-8u74-linux-x64.tar.gz
ENV JDK_FOLDER jdk1.8.0_74

ENV JAVA_HOME /usr/share/java/
ENV PATH ${PATH}:${JAVA_HOME}/bin

# Install bash and curl and clean cache
RUN apk --update add bash curl && \
    rm -rf /var/cache/apk/*

# Download and install glibc
RUN curl -Ls ${GLIBC_ROOT_URL}/${GLIBC_FILE} -o /tmp/${GLIBC_FILE} && \
    apk add --allow-untrusted /tmp/${GLIBC_FILE} && \
    rm /tmp/${GLIBC_FILE}

# Download and install java
RUN curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" ${JDK_ROOT_URL} | \
    tar -xzf - -C /usr/share | \
    ln -sf /usr/share/${JDK_FOLDER} /usr/share/java | \
    rm -rf ${JAVA_HOME}/lib/visualvm/ \
             ${JAVA_HOME}/lib/missioncontrol/ \
             ${JAVA_HOME}/*src.zip

CMD ["/bin/bash"]