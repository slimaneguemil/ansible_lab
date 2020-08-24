FROM ubuntu:20.04

MAINTAINER Alexandre Coilier "https://github.com/acoilier"

ENV pip_packages "ansible pyopenssl"

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       locales \
       python3-software-properties \
       software-properties-common \
       python-setuptools \
       wget \
       rsyslog \
       systemd \
       systemd-cron \
       sudo \
       iproute2 \
       ssh \
       sshpass \
       curl\
       python3-pip \
       apt-utils \
       iputils-ping \
    && rm -Rf /var/lib/apt/lists/* \
    && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
    && apt-get clean

RUN sed -i 's/^\($ModLoad imklog\)/#\1/' /etc/rsyslog.conf

RUN locale-gen en_US.UTF-8

RUN pip3 install $pip_packages

VOLUME ["/sys/fs/cgroup", "/tmp", "/run"]

CMD [ "ansible-playbook", "--version" ]