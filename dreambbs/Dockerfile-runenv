FROM centos:6
MAINTAINER holishing

# This is for building DreamBBS runtime environment for executables
RUN rm /etc/localtime \
    && ln -s /usr/share/zoneinfo/Asia/Taipei /etc/localtime \
    && yum update -y \
    && yum clean all \
    && yum install --nogpgcheck -y \
                util-linux-ng \
                glibc.i686 \
                ncurses-devel.i686 \
                cronie

# Add group and user named bbs
RUN groupadd --gid 9999 bbs \
    && useradd -g bbs -s /bin/bash --uid 9999 bbs

# Notice, in here, mbbsd started service and PROVIDE BIG5 encoding for users.
CMD ["sh","-c","service crond start && while true; do sleep 10; done"]
