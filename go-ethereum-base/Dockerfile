FROM ubuntu:14.04

# Exporting variables...
ENV HOME /root
ENV GOPATH /root/go
ENV PATH /root/go/bin:/usr/local/go/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

# GOPATH
RUN mkdir -p /root/go

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -qy git mercurial software-properties-common
RUN apt-get install -qy ubuntu-sdk libgmp3-dev libreadline6-dev
RUN apt-get install -qy golang

RUN add-apt-repository ppa:ubuntu-sdk-team/ppa
RUN apt-get update
RUN apt-get install -qy qtbase5-private-dev qtdeclarative5-private-dev libqt5opengl5-dev

