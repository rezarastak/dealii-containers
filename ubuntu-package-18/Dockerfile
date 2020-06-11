FROM ubuntu:18.04
LABEL maintainer="reza.rastak@gmail.com"
RUN adduser --disabled-password --gecos '' dealii
RUN add-apt-repository ppa:ginggs/deal.ii-backports && \
    apt-get update -q && apt-get install -y -q \
      software-properties-common \
      ssh \
      ninja-build \
      libdeal.ii-dev
