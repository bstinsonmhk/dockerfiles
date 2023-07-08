FROM quay.io/centos/centos:stream8

MAINTAINER Brian Stinson <brian@bstinson.com>

RUN yum -y install epel-release
RUN yum -y update

RUN yum clean all
RUN yum -y --setopt=tsflags=nodocs install python3 bpython python3-setuptools python3-pip sudo yum-utils git vim-enhanced wget mock centos-packager python3-GitPython python3-click python3-PyYAML python3-requests python3-rfc3986 python3-texttable

COPY armhfp-mbox-koji.conf /etc/koji.conf.d/
COPY mbox-koji.conf /etc/koji.conf.d/
COPY centos-server-ca.crt /etc/pki/ca-trust/source/anchors/
RUN update-ca-trust

RUN useradd -m bstinson
RUN usermod -a -G mock bstinson
RUN echo 'bstinson ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/mbox && chmod 600 /etc/sudoers.d/mbox
RUN echo '172.22.0.106    koji.mbox.centos.org' >> /etc/hosts
RUN echo '172.22.0.106    mbs.mbox.centos.org' >> /etc/hosts
RUN ln -svf /usr/bin/koji /usr/bin/armhfp-mbox 
RUN ln -svf /usr/bin/koji /usr/bin/mbox 

USER bstinson
WORKDIR /home/bstinson
CMD /bin/bash -l
