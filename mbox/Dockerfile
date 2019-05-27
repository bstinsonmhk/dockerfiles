FROM centos:7

MAINTAINER Brian Stinson <brian@bstinson.com>

RUN yum -y install epel-release
RUN yum -y update

RUN yum clean all
RUN yum -y --setopt=tsflags=nodocs install python python34 bpython python-setuptools python-pip sudo yum-utils git vim-enhanced wget mock ctags-etags centos-packager

COPY armhfp-mbox-koji.conf /etc/koji.conf.d/
COPY mbox-koji.conf /etc/koji.conf.d/

RUN useradd -m mbox
RUN usermod -a -G mock mbox
RUN echo 'mbox ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/mbox && chmod 600 /etc/sudoers.d/mbox
RUN ln -svf /usr/bin/koji /usr/bin/armhfp-mbox 
RUN ln -svf /usr/bin/koji /usr/bin/mbox 

USER mbox
WORKDIR /home/mbox
CMD /bin/bash -l
