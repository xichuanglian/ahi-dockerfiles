# Mongodb for Asset Allocation

# Use centos7.2 from Aliyun's registry
FROM w6wy7kfr.mirror.aliyuncs.com/library/centos:centos7.2.1511

MAINTAINER Da Wei, xichuanglian@gmail.com

RUN yum -y update
RUN yum -y install epel-release
RUN yum -y install mongodb mongodb-server

ADD mongod.conf /etc/mongod.conf

VOLUME ["/data"]
RUN chown -R mongodb:mongodb /data
USER mongodb
EXPOSE 27017

CMD ["-f", "/etc/mongod.conf"]
ENTRYPOINT ["mongod"]