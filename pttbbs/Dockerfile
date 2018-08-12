FROM debian:stretch
MAINTAINER holishing

RUN apt update \
    && apt upgrade -y \
    && apt-get install -y --no-install-recommends \
        bmake \
        ccache \
        clang \
        git \
        ca-certificates \
        libevent-dev \
        pkg-config \
        python

RUN groupadd --gid 99 bbs \
    && useradd -g bbs -s /bin/bash --uid 9999 bbs \
    && mkdir /home/bbs \
    && chown -R bbs:bbs /home/bbs

USER bbs
ENV HOME=/home/bbs

RUN cd /home/bbs \
    && git clone http://github.com/ptt/pttbbs \
    && cd /home/bbs/pttbbs \
    && cp sample/pttbbs.conf /home/bbs/pttbbs/pttbbs.conf
RUN echo '#define TIMET64' >> /home/bbs/pttbbs/pttbbs.conf 
RUN echo '#define SHMALIGNEDSIZE (1048576*4)' >> /home/bbs/pttbbs/pttbbs.conf
RUN cd /home/bbs/pttbbs && bmake all install clean

RUN cd /home/bbs/pttbbs/sample \
    && bmake install \
    && /home/bbs/bin/initbbs -DoIt

# Notice, in here, mbbsd started service and PROVIDE UTF-8 encoding for users, if you prefer BIG-5, just remove `-e utf8`.
CMD ["sh","-c","/home/bbs/bin/shmctl init && /home/bbs/bin/mbbsd -d -e utf8 -p 8888 && while true; do sleep 10; done"]
EXPOSE 8888
