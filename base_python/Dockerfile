FROM centos:7

WORKDIR /opt/

ENV py_version=3.6.1

RUN localedef -c -f UTF-8 -i zh_CN zh_CN.UTF-8         \
    && echo 'LANG="zh_CN.UTF-8"' > /etc/locale.conf    \
    && echo 'LANG="zh_CN.UTF-8"' > /etc/sysconfig/i18n \
    && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime  \
    && echo "Asia/Shanghai" > /etc/timezone  \
    && yum -y install  wget unzip  xz gcc make automake zlib-devel openssl-devel epel-release sqlite-devel    \
    && rm -rf /var/cache/yum/*                         \
    && wget https://www.python.org/ftp/python/3.6.1/Python-${py_version}.tar.xz -O /opt/Python-${py_version}.tar.xz     \
    && tar xf Python-${py_version}.tar.xz                      \
    && cd Python-${py_version}                                 \
    && ./configure                                     \
    && make                                            \
    && make install                                    \
    && rm -rf /opt/Python-${py_version}*               

ENV LC_ALL=zh_CN.UTF-8     
ENV LANG=zh_CN.UTF-8
ENV LANGUAGE=zh_CN.UTF-8

RUN python3 -m venv py3
