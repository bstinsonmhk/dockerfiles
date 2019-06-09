FROM centos:7

MAINTAINER Brian Stinson <brian@bstinson.com>

RUN yum -y install epel-release
RUN yum -y update

RUN yum clean all
RUN yum -y --setopt=tsflags=nodocs install python python34 bpython python-setuptools python-pip sudo yum-utils git mercurial vim-enhanced wget mock ctags-etags zsh

RUN useradd -m bstinson 
RUN usermod -a -G mock bstinson
RUN echo 'bstinson ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/bstinson && chmod 600 /etc/sudoers.d/bstinson
RUN mkdir -p /home/bstinson/src && chown bstinson.bstinson /home/bstinson/src

USER bstinson
WORKDIR /home/bstinson
RUN git clone https://bitbucket.org/bstinsonmhk/dotfiles.git ~/.dotfiles
RUN ~/.dotfiles/makehomedir.sh
CMD /bin/zsh -l
