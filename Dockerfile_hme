FROM centos:latest

LABEL maintainer="Herve dockerlite@gmail.com"

# --- Mise a jour et installation des paquets
RUN yum -y update && \
    yum -y install "@Development" && \
    yum -y install git epel-release wget dh-autoreconf curl-devel expat-devel gettext-devel && \
    yum -y install openssl-devel perl-devel zlib-devel && \
    yum -y install asciidoc xmlto docbook2X getopt

#  --- lien symbolique
RUN ln -s /usr/bin/db2x_docbook2texi /usr/bin/docbook2x-texi

WORKDIR /projects

# installation de la derniere version de git
RUN git clone https://github.com/git/git.git
WORKDIR /projects/git
RUN git checkout tags/$(git describe --tags $(git rev-list --tags --max-count=1))

# -- compilation des sources et de la doc
RUN   make configure && \
      ./configure --prefix=/usr && \
      make all doc info && \
      make install install-doc install-html install-info

# -- commande de verification
CMD ["git","--version"]
