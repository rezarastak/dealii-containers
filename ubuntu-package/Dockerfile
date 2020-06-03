FROM ubuntu:latest
LABEL maintainer="reza.rastak@gmail.com"
RUN TZ="America/Los_Angeles" DEBIAN_FRONTEND="noninteractive" \
    apt-get update -q && apt-get upgrade -y -q && \
    apt-get install -y -q software-properties-common ssh ninja-build libdeal.ii-dev
RUN adduser --disabled-password --gecos '' dealii
