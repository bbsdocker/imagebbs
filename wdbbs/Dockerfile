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
        bmake \
        ccache \
        clang \
	curl \
        ca-certificates \
	gcc-multilib \
	lib32ncurses5-dev

USER bbs
ENV HOME=/home/bbs

RUN cd /home/bbs \
    && sh -c "curl -L  https://github.com/clamtestbbs/wdbbs/archive/204ffe6740ae7bb4541778064b7a42b0f85b0171.tar.gz | tar -zxv" \
    && mv wdbbs-204ffe6740ae7bb4541778064b7a42b0f85b0171 wdbbs \
    && cd /home/bbs/wdbbs \
    && cp -r sample/bbs /home

COPY file/wdbbs_conf /home/bbs/wdbbs/wdbbs.conf
RUN cd /home/bbs/wdbbs && bmake all install clean

# Notice, in here, mbbsd started service and PROVIDE BIG-5 encoding for users.
CMD ["sh","-c","/home/bbs/bin/mbbsd 8888 && while true; do sleep 10; done"]
EXPOSE 8888
