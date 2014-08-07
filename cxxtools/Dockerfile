# DOCKER-VERSION 0.3.4
# image olafradicke/cxxtools
FROM fedora:20
MAINTAINER Olaf Raicke <olaf@atix.de>


RUN yum -y install gcc-c++ make wget
RUN yum -y install libtool mysql++-devel sqlite-devel openssl-devel postgresql-devel

WORKDIR /tmp
RUN  wget www.tntnet.org/download/cxxtools-2.2.1.tar.gz
RUN  tar -xzf  cxxtools-2.2.1.tar.gz
WORKDIR /tmp/cxxtools-2.2.1
RUN /usr/bin/ls -lah
RUN  /bin/bash ./configure
RUN  make
RUN  make install

RUN  echo "/usr/local/lib" >  /etc/ld.so.conf.d/cxxtools.conf
RUN  ldconfig




VOLUME ["/var/cxxtools/docker/workspace/"]
