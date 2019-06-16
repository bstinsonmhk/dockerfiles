FROM fedora:28

MAINTAINER Brian Stinson <brian@bstinson.com>

RUN dnf -y update

RUN dnf -y install python bpython python-setuptools python-pip sudo git hub mercurial neovim python3-neovim wget mock zsh findutils ctags-etags pytest
RUN dnf clean all

RUN useradd -m bstinson 
RUN usermod -a -G mock bstinson
RUN echo 'bstinson ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/bstinson && chmod 600 /etc/sudoers.d/bstinson
RUN mkdir -p /home/bstinson/src && chown bstinson.bstinson /home/bstinson/src

USER bstinson
WORKDIR /home/bstinson
RUN git clone https://bitbucket.org/bstinsonmhk/dotfiles.git ~/.dotfiles
RUN ~/.dotfiles/makehomedir.sh
CMD /bin/zsh -l
