FROM centos:7

WORKDIR /opt

ENV luna_version 1.4.0

RUN yum -y install wget epel-release   \
    && yum -y install nginx            \
    && wget https://github.com/jumpserver/luna/releases/download/${luna_version}/luna.tar.gz -O /opt/luna.tar.gz \
    && tar zxf luna.tar.gz \
    && chown -R root:root luna  \
    && rm -rf /opt/luna.tar.gz   \
    && rm -rf /var/cache/yum/*

EXPOSE 80

CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
