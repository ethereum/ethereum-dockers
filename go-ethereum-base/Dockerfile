FROM ubuntu:14.04

# Export GOPATH
ENV GOPATH /root/go
ENV PATH /root/go/bin:$PATH

# GOPATH
RUN mkdir -p /root/go

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -qy git mercurial software-properties-common
RUN apt-get install -qy libgmp3-dev libreadline6-dev
RUN apt-get install -qy build-essential
RUN apt-get install -qy golang

# Qt5
RUN add-apt-repository ppa:ethereum/ethereum-qt
RUN apt-get update
RUN apt-get install -qy qt5-default, libqt5qml5, libqt5quick5, libqt5webengine5, qml-module-qtquick-controls, qml-module-qtquick-dialogs
