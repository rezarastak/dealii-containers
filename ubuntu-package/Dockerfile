FROM ubuntu:bionic
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get install -y -q software-properties-common && \
    add-apt-repository ppa:ginggs/deal.ii-backports && apt-get update && \
    apt-get install -y -q libdeal.ii-dev
