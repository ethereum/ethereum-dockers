FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -qy build-essential g++-4.8 git cmake libboost-all-dev
RUN apt-get install -qy automake unzip libgmp-dev libtool libleveldb-dev yasm libminiupnpc-dev libreadline-dev scons
RUN apt-get install -qy libncurses5-dev libcurl4-openssl-dev

RUN git clone --depth=1 https://github.com/mmoss/cryptopp.git
RUN cd cryptopp && scons --shared --prefix=/usr

RUN git clone --depth=1 https://github.com/cinemast/libjson-rpc-cpp.git
RUN cd libjson-rpc-cpp/build && cmake .. && make && make install
