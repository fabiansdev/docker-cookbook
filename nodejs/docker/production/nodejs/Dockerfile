FROM centos:centos7
MAINTAINER diego.uribe.gamez@gmail.com

RUN yum -y update
RUN yum -y install wget
RUN yum -y install epel-release
RUN yum -y install gcc gcc-c++
RUN yum -y install make
RUN yum -y install mongodb
RUN yum clean all

RUN mkdir node-latest
RUN cd node-latest && wget http://nodejs.org/dist/v4.6.0/node-v4.6.0.tar.gz
RUN cd node-latest && tar xvf node-v4.6.0.tar.gz && rm node-v4.6.0.tar.gz
RUN cd node-latest && cd * && ./configure
RUN cd node-latest && cd * && make
RUN cd node-latest && cd * && make install
RUN ln -s /usr/local/bin/node /usr/bin/node
RUN ln -s /usr/local/bin/npm /usr/bin/npm
RUN cd ../../ && rm node-latest/ -r -f

RUN npm install -g node-inspector supervisor forever

COPY app/ /opt/app/
RUN cd /opt/app/ && npm install
