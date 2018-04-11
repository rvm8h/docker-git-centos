FROM centos:latest
MAINTAINER Lorenzo <lorenzo.it@outlook.com>

WORKDIR /git-2.17.0/

RUN yum -y update && \
    yum -y install wget dh-autoreconf curl-devel expat-devel gettext-devel openssl-devel perl-devel zlib-devel asciidoc xmlto docbook2X getopt && \
    wget https://github.com/git/git/archive/v2.17.0.tar.gz && \
    tar -zxf v2.17.0.tar.gz && \
    yum -y remove wget && \
    ln -s /usr/bin/db2x_docbook2texi /usr/bin/docbook2x-texi && \
    cd git-2.17.0 && \
    yum -y install make && \
    yum -y install autoconf && \
    yum -y install gcc && \
    make configure && \
    ./configure --prefix=/usr && \
    make -j$(nproc) all
    make install
CMD ["git","--version"]
