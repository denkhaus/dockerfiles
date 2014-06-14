
FROM ubuntu:14.04
MAINTAINER denkhaus <peristaltic@gmx.net>

ENV DIR /bs 
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y cmake git nano libncurses5-dev libreadline-dev uuid-dev g++ libdb++-dev \
	 libdb-dev zip libssl-dev openssl build-essential python-dev autotools-dev \
	 libicu-dev build-essential libbz2-dev libboost-dev libboost-all-dev; \
	 apt-get clean;	 


RUN git clone https://github.com/BitShares/bitshares_toolkit.git $DIR 

ENV BS_REVISION 201406142207
RUN cd $DIR && git submodule update --init && git pull --all && cmake . && make clean && make

ENV BS_CONFIG_REVISION 201406132329                                                          
ADD .BitSharesXTS /.BitSharesXTS

WORKDIR /bs/programs/client/
EXPOSE 5679 5680 8764
ENTRYPOINT /bs/programs/client/bitshares_client --server --p2p-port 8764
