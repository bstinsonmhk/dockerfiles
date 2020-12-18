FROM registry.access.redhat.com/ubi8:latest

RUN rpm -ivh --replacefiles http://mirror.centos.org/centos/8-stream/BaseOS/x86_64/os/Packages/centos-stream-release-8.4-1.el8.noarch.rpm \
                            http://mirror.centos.org/centos/8-stream/BaseOS/x86_64/os/Packages/centos-stream-repos-8-2.el8.noarch.rpm \
                            http://mirror.centos.org/centos/8-stream/BaseOS/x86_64/os/Packages/centos-gpg-keys-8-2.el8.noarch.rpm \
    && rpm -e redhat-release \
    && dnf --setopt=tsflags=nodocs --setopt=install_weak_deps=false -y distro-sync \
    && dnf remove -y subscription-manager dnf-plugin-subscription-manager\
    && dnf clean all \
    && rm -f /etc/yum.repos.d/ubi.repo
