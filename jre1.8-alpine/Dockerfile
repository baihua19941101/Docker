################################################################
##基于bhcaptain/base-alpine:3.7构建jre镜像
##jre版本: jre-8u221-linux-x64.tar.gz
##Alpine版本： 3.7
################################################################
FROM bhcaptain/base-alpine:3.7
MAINTAINER baihua(969865525@qq.com)
COPY jre-8u221-linux-x64.tar.gz /tmp
RUN echo http://mirrors.ustc.edu.cn/alpine/v3.7/main > /etc/apk/repositories  \  
    && echo http://mirrors.ustc.edu.cn/alpine/v3.7/community >> /etc/apk/repositories  \
 	&& apk update && apk upgrade  \
	&& apk --no-cache add ca-certificates \
	&& wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub \
	&& wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-2.28-r0.apk \
	&& apk add glibc-2.28-r0.apk \
	&& rm glibc-2.28-r0.apk \
	&& tar -xf /tmp/jre-8u221-linux-x64.tar.gz -C /tmp/ \
	&& mkdir -p /usr/lib/jvm \
	&& mv /tmp/jre1.8.0_221/*  /usr/lib/jvm/ \
	&& rm -rf /tmp/* \
	&& rm -rf /var/cache/apk/*
# 设置 jre 的环境变量
ENV JAVA_HOME /usr/lib/jvm
ENV CLASSPATH .:$JAVA_HOME/lib
ENV PATH $PATH:$JAVA_HOME/bin  

