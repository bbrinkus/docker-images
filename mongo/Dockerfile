FROM alpine:3.3
MAINTAINER Balazs Brinkus <balazs@brinkus.com>
LABEL Description="Alpine Linux with Mongo DB (/data external mount point)"

# Overwrite repositories and use the edge
RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/main" > /etc/apk/repositories && \
    echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories && \
    echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories

# Install bash and mongodb 3.2.4
RUN apk --update add bash \
    mongodb && \
    rm -rf /var/cache/apk/*

# Change sys settings
#RUN echo "never" > /sys/kernel/mm/transparent_hugepage/enabled && \
#    echo "never" > /sys/kernel/mm/transparent_hugepage/defrag

# Create the data directory
RUN mkdir -p /data/db

# Create an external mount point
VOLUME ["/data"]

# Expose default port
EXPOSE 27017

# Run the mongo db
ENTRYPOINT ["/usr/bin/mongod"]