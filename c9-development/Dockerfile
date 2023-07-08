FROM quay.io/centos/centos:stream9

MAINTAINER Brian Stinson <brian@bstinson.com>

RUN dnf -y update

RUN dnf clean all
RUN dnf -y --setopt=tsflags=nodocs install python3 python3-setuptools python3-pip sudo dnf-utils git vim-enhanced wget zsh

RUN useradd -m bstinson 
RUN echo 'bstinson ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/bstinson && chmod 600 /etc/sudoers.d/bstinson
RUN mkdir -p /home/bstinson/src && chown bstinson.bstinson /home/bstinson/src

USER bstinson
WORKDIR /home/bstinson
RUN git clone https://bitbucket.org/bstinsonmhk/dotfiles.git ~/.dotfiles
RUN ~/.dotfiles/makehomedir.sh
CMD /bin/zsh -l
