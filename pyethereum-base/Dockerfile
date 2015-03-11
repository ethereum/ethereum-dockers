FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -qy curl git python2.7 python-dev build-essential wget

RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py
