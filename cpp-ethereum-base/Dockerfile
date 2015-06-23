FROM ubuntu:14.04.2

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -qy build-essential g++-4.8 git cmake libboost-all-dev
RUN apt-get install -qy automake unzip libgmp-dev libtool libleveldb-dev yasm libminiupnpc-dev libreadline-dev scons
RUN apt-get install -qy libncurses5-dev libcurl4-openssl-dev wget
RUN apt-get install -qy libjsoncpp-dev libargtable2-dev libmicrohttpd-dev
RUN apt-get install -qy pkg-config

# Ethereum PPA
RUN apt-get install -qy software-properties-common
RUN add-apt-repository -y ppa:ethereum/ethereum
RUN add-apt-repository -y ppa:ethereum/ethereum-dev
RUN apt-get update
RUN apt-get install -qy libcryptopp-dev libjson-rpc-cpp-dev

# LLVM
RUN wget -O - http://llvm.org/apt/llvm-snapshot.gpg.key|sudo apt-key add -
RUN echo "deb http://llvm.org/apt/trusty/ llvm-toolchain-trusty main" > /etc/apt/sources.list.d/llvm-trusty.list
RUN apt-get update
RUN apt-get install -qy llvm-3.5-dev llvm-3.7-dev libedit-dev libz-dev

# Qt5
RUN add-apt-repository ppa:ethereum/ethereum-qt
RUN apt-get update
RUN apt-get install -qy qml-module-qtquick-controls qml-module-qtquick-dialogs libqt5webengine5-dev

# DAG
RUN apt-get install -qy eth
RUN eth --create-dag 0
RUN apt-get remove -qy eth
RUN add-apt-repository -ry ppa:ethereum/ethereum-dev
RUN apt-get update
