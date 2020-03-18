FROM ubuntu:18.04
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && \
    apt-get install -y -q software-properties-common ssh && \
    add-apt-repository ppa:ginggs/deal.ii-backports && apt-get update && \
    apt-get install -y -q libdeal.ii-dev
