FROM ubuntu:latest
LABEL maintainer="reza.rastak@gmail.com"
RUN adduser --disabled-password --gecos '' dealii
RUN apt-get update -q && \
    TZ="America/Los_Angeles" DEBIAN_FRONTEND="noninteractive" apt-get install -y -q \
      build-essential \
      software-properties-common \
      ssh \
      ninja-build \
      libdeal.ii-dev
