FROM centos

MAINTAINER paimpozhil@gmail.com

RUN yum -y install wget

RUN rpm -Uvh   http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm

RUN rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm

RUN yum -y install openssh-server

RUN yum -y install x2goserver x2goserver-xsession x2golxdebindings pwgen firefox pulseaudio libcurl3 

RUN yum -y groupinstall Xfce

## fix the locale crap 
RUN yum -y reinstall glibc-common

RUN chkconfig sshd on

RUN sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config
RUN sed -i "s/#PermitRootLogin/PermitRootLogin/g" /etc/ssh/sshd_config

RUN echo 'root:changeme' | chpasswd

RUN service sshd start

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]
