################################################################
##基于bhcaptain/base-alpine:3.10构建jre镜像
##jre版本: jre-8u221-linux-x64.tar.gz
##Alpine版本： 3.10
###字符集为：zh_CN.UTF-8
################################################################
FROM bhcaptain/alpine:3.10
MAINTAINER baihua(969865525@qq.com)
COPY jre-8u221-linux-x64.tar.gz /tmp 
RUN  apk update && apk upgrade  \
	&& apk --no-cache add  curl bash  tzdata \
        && /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
	&& tar -xf /tmp/jre-8u221-linux-x64.tar.gz -C /tmp/ \
	&& mkdir -p /usr/lib/jvm \
	&& mv /tmp/jre1.8.0_221/*  /usr/lib/jvm/ \
	&& rm -rf /tmp/* \
	&& rm -rf /var/cache/apk/*
# 设置 jre 的环境变量
ENV JAVA_HOME /usr/lib/jvm
ENV CLASSPATH .:$JAVA_HOME/lib
ENV PATH $PATH:$JAVA_HOME/bin  
