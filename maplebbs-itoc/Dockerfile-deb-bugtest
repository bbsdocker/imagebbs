FROM debian:stretch
MAINTAINER holishing

RUN groupadd --gid 99 bbs \
    && useradd -g bbs -s /bin/bash --uid 9999 bbs \
    && mkdir /home/bbs \
    && chown -R bbs:bbs /home/bbs \
    && rm /etc/localtime \
    && ln -s /usr/share/zoneinfo/Asia/Taipei /etc/localtime

RUN apt update \
    && apt upgrade -y \
    && apt-get install -y --no-install-recommends \
	patch \
	make \
	curl \
        ca-certificates \
	gcc-multilib \
	lib32ncurses5-dev

RUN apt-get install -y --no-install-recommends 

USER bbs
ENV HOME=/home/bbs

RUN cd /home/bbs \
    && sh -c "curl -L https://github.com/xeonchen/maplebbs-itoc/archive/5deda091832277d1997489d6572a5415aa7a242f.tar.gz|tar -zxv" \
    && mv maplebbs-itoc-5deda091832277d1997489d6572a5415aa7a242f maplebbs-itoc \
    && cp -r /home/bbs/maplebbs-itoc/bbs /home/

WORKDIR /home/bbs/patch
COPY file/patch-for64bit-Makefile /home/bbs/patch/patch-for64bit-Makefile
COPY file/config_h /home/bbs/src/include/config.h
RUN patch -p1 -d /home/bbs/src </home/bbs/patch/patch-for64bit-Makefile
RUN cd /home/bbs/src && make linux install clean

# Notice, in here, mbbsd started service and PROVIDE BIG5 encoding for users.
CMD ["sh","-c","/home/bbs/bin/account &&  /home/bbs/bin/camera && /home/bbs/bin/bbsd 8888 && while true; do sleep 10; done"]
EXPOSE 8888

