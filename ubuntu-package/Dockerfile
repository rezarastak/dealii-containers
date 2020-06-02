FROM ubuntu:latest
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get upgrade -y -q && \
    apt-get install -y -q software-properties-common ssh ninja-build && \
    add-apt-repository ppa:ginggs/deal.ii-backports && apt-get update && \
    apt-get install -y -q libdeal.ii-dev
RUN adduser --disabled-password --gecos '' dealii
