FROM debian:8
MAINTAINER "Paolo Smiraglia <paolo.smiraglia@gmail.com>"

# install dependencies
RUN apt-get update \
    && apt-get install -y -q \
        curl \
        git \
        vim

# add SaltStack repo
ADD conf/saltstack.list /etc/apt/sources.list.d/saltstack.list

# install SaltStack
RUN curl https://repo.saltstack.com/apt/debian/8/amd64/latest/SALTSTACK-GPG-KEY.pub | apt-key add - \
    && apt-get update \
    && apt-get install -y -q \
        salt-minion

# add minion's configuration modules
ADD conf/minion.d/* /etc/salt/minion.d/

# add top level states
ADD conf/salt /srv/salt

# add top level pillar
ADD conf/pillar /srv/pillar

# create formulas' directory
RUN mkdir -p /srv/formulas

