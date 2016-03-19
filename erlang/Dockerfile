FROM alpine:3.3
MAINTAINER Balazs Brinkus <balazs@brinkus.com>
LABEL Description="Alpine Linux with Erlang 18"

# Use the edge repositories
RUN echo -e "@edge-main http://dl-cdn.alpinelinux.org/alpine/edge/main\n@edge-community http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories

# Install bash and erlang packages from the edge
RUN apk --update add bash \
    erlang-kernel@edge-community \
    erlang-stdlib@edge-community \
    erlang-compiler@edge-community \
    erlang@edge-community \
    erlang-tools@edge-community && \
    rm -rf /var/cache/apk/*

CMD ["/bin/bash"]
