FROM ubuntu:xenial

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -qy git mercurial software-properties-common
RUN apt-get install -qy libgmp3-dev libreadline6-dev
RUN apt-get install -qy build-essential

# golang
RUN apt-get install -qy golang
