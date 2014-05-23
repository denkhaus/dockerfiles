
FROM ubuntu:14.04
MAINTAINER denkhaus <peristaltic@gmx.net>

# Hack for initctl not being available in Ubuntu
RUN dpkg-divert --local --rename --add /sbin/initctl
RUN ln -fs /bin/true /sbin/initctl


RUN apt-get update
RUN sudo apt-get install -y cmake git libreadline-dev uuid-dev g++ libdb++-dev libdb-dev zip libssl-dev openssl build-essential python-dev autotools-dev libicu-dev build-essential libbz2-dev libboost-dev libboost-all-dev
RUN git clone https://github.com/BitShares/bitshares_toolkit.git
RUN cd bitshares_toolkit
RUN git submodule init
RUN git submodule update
cmake .
make

