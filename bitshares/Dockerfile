
FROM ubuntu:14.04
MAINTAINER denkhaus <peristaltic@gmx.net>

ENV DIR bs 
ENV DEBIAN_FRONTEND noninteractive
# Hack for initctl not being available in Ubuntu
#RUN dpkg-divert --local --rename --add /sbin/initctl
#RUN ln -fs /bin/true /sbin/initctl

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y cmake git nano libncurses5-dev libreadline-dev uuid-dev g++ libdb++-dev \
	 libdb-dev zip libssl-dev openssl build-essential python-dev autotools-dev \
	 libicu-dev build-essential libbz2-dev libboost-dev libboost-all-dev


RUN git clone https://github.com/BitShares/bitshares_toolkit.git $DIR && cd $DIR && git submodule update --init 
RUN cd $DIR && cmake -DCURSES_LIBRARY=/usr/lib/x86_64-linux-gnu/libncurses.so -DCURSES_INCLUDE_PATH=/usr/include/ . #curses missing 
RUN cd $DIR && make 

EXPOSE 5679 5680
#ENTRYPOINT  cd $DIR/programs/client/ && ./bitshares_client --server




