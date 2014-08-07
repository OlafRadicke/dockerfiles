# DOCKER-VERSION 0.3.4
# image olafradicke/tntdb
FROM olafradicke/cxxtools:latest
MAINTAINER Olaf Raicke <olaf@atix.de>


ENV MYSQL-SUPPORT yes
ENV POSTGRESQL-SUPPORT yes
ENV SQLITE-SUPPORT yes
ENV REPLICATION_SUPPORT yes
ENV ORACLE-SUPPORT no

RUN yum -y install gcc-c++ make wget

RUN yum -y install mysql++-devel sqlite-devel  postgresql-devel
WORKDIR /tmp/
RUN  wget www.tntnet.org/download/tntdb-1.3.tar.gz
RUN  tar -xzf  tntdb-1.3.tar.gz
WORKDIR /tmp/tntdb-1.3
RUN  /bin/bash ./configure --with-mysql=$MYSQL-SUPPORT --with-postgresql=$POSTGRESQL-SUPPORT --with-sqlite=$SQLITE-SUPPORT  --with-replication=$REPLICATION_SUPPORT --with-oracle=$ORACLE-SUPPORT
RUN  make
RUN  make install

RUN  echo "/usr/local/lib" >  /etc/ld.so.conf.d/tntdb.conf
RUN  ldconfig

VOLUME ["/var/tntdb/docker/workspace/"]
