FROM centos:6

MAINTAINER Brian Stinson <brian@bstinson.com>

RUN yum -y clean all
RUN yum -y install epel-release sudo

RUN useradd -m bstinson -u 1000
RUN echo 'bstinson ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/bstinson
RUN mkdir -p /home/bstinson/src && chown bstinson.bstinson /home/bstinson/src

USER bstinson
WORKDIR /home/bstinson
CMD /bin/bash -l
