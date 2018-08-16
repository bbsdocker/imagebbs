#This is a repo form maplebbs-itoc FORKed, not official release

FROM centos:7
MAINTAINER holishing

RUN yum update -y && \
    yum install --nogpgcheck -y \
                gcc \
                make \
                vim \
                clang \
		glibc-devel \
                glibc-devel.i686 \
                libgcc.i686 \
                libstdc++-devel.i686 \
                ncurses-devel.i686

RUN groupadd --gid 9999 bbs \
    && useradd -g bbs -s /bin/bash --uid 9999 bbs

USER bbs
ENV HOME=/home/bbs

RUN cd /home/bbs \
    && sh -c "curl -L https://github.com/clamtestbbs/maplebbs-clam/archive/2c6fe4c51c1cba988cb018002bf380ae5c9c2974.tar.gz|tar -zxv" \
    && mv maplebbs-clam-2c6fe4c51c1cba988cb018002bf380ae5c9c2974 maplebbs-clam \
    && cp -r /home/bbs/maplebbs-clam/sample/bbs /home/
COPY config_h /home/bbs/maplebbs-clam/include/config.h
RUN cd /home/bbs/maplebbs-clam && make linux install clean

# Notice, in here, mbbsd started service and PROVIDE BIG5 encoding for users.
CMD ["sh","-c","/home/bbs/bin/account &&  /home/bbs/bin/camera && /home/bbs/bin/bbsd 8888 && while true; do sleep 10; done"]
EXPOSE 8888
