FROM python:3.9.6-alpine

RUN apk update \
    && apk add --no-cache openssh-server iputils sshpass openssl curl git gcc libffi-dev libc-dev docker openrc \
    && pip3 install ansible paramiko molecule[docker] yamllint ansible-lint flake8 \
    && apk del gcc

RUN ansible-galaxy collection install -v community.docker:>=1.9.1

RUN export ANSIBLE_HOST_KEY_CHECKING=False
#RUN rc-update add docker boot && service docker start
