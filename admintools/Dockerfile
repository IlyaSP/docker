FROM alpine:3.15.4

ARG PACKEGES="openssh iputils curl git busybox-extras openrc bind-tools tcptraceroute nano"
#ARG PACKEGES="openssh-server iputils"

RUN apk update \
    && apk add --no-cache $PACKEGES
