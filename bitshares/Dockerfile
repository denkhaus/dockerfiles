
FROM denkhaus/ubuntu-latest-dev
MAINTAINER denkhaus <peristaltic@gmx.net>

ENV DIR bs 
# Hack for initctl not being available in Ubuntu
#RUN dpkg-divert --local --rename --add /sbin/initctl
#RUN ln -fs /bin/true /sbin/initctl

RUN sudo apt-get update
RUN sudo apt-get upgrade -y
RUN git clone https://github.com/BitShares/bitshares_toolkit.git $DIR
RUN cd $DIR && git submodule update --init 
RUN cd $DIR && cmake . 
RUN cd $DIR && make

EXPOSE 5679 5680
ENTRYPOINT  cd $DIR/programs/client/ && ./bitshares_client --server
