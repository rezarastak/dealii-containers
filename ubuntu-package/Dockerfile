ARG UBUNTU_DOCKER_IMAGE=ubuntu:latest
FROM $UBUNTU_DOCKER_IMAGE
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && \
    TZ="America/Los_Angeles" DEBIAN_FRONTEND="noninteractive" apt-get install -y -q \
      build-essential \
      software-properties-common \
      ssh \
      ninja-build \
      libdeal.ii-dev
