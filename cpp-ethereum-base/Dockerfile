FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -qy build-essential g++-4.8 git cmake libboost-all-dev
RUN apt-get install -qy automake unzip libgmp-dev libtool libleveldb-dev yasm libminiupnpc-dev libreadline-dev scons
RUN apt-get install -qy libncurses5-dev libcurl4-openssl-dev wget
RUN apt-get install -qy qtbase5-dev qt5-default qtdeclarative5-dev libqt5webkit5-dev

RUN git clone --depth=1 https://github.com/mmoss/cryptopp.git
RUN cd cryptopp && scons --shared --prefix=/usr

RUN apt-get install -qy libjsoncpp-dev libargtable2-dev
RUN git clone --depth=1 https://github.com/cinemast/libjson-rpc-cpp.git
RUN cd libjson-rpc-cpp && git checkout eaca2481e2889d5a5b748383fb02b1d395969cd4
# Patch to add Access-Control-Allow-Origin: * in headers
# RUN wget https://gist.githubusercontent.com/caktux/b876fb0bf638f02387a8/raw/ea7db7cfcf8223acfdaf0b60626e592f5ed7836a/jsonrpc-allow-origin.patch
# RUN cd libjson-rpc-cpp && patch -p1 < ../jsonrpc-allow-origin.patch
RUN mkdir libjson-rpc-cpp/build && cd libjson-rpc-cpp/build && cmake .. && make && make install
