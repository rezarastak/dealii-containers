FROM ubuntu:bionic
MAINTAINER reza.rastak@gmail.com
RUN apt-get update && apt-get install -y software-properties-common && \
    add-apt-repository ppa:ginggs/deal.ii-backports && apt-get update && \
    apt-get install -y libdeal.ii-dev
