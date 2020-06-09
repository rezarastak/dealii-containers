FROM ubuntu:latest
LABEL maintainer="reza.rastak@gmail.com"
ENV CANDI_DIR=/candi CANDI_SRC=/candi-src
COPY local.cfg $CANDI_DIR/
RUN adduser --disabled-password --gecos '' dealii && \
    apt-get update -q && apt-get upgrade -y -q && \
    TZ="America/Los_Angeles" DEBIAN_FRONTEND="noninteractive" \
      apt-get install -y -q build-essential python bc ninja-build lsb-release wget numdiff \
      automake autoconf gfortran openmpi-bin openmpi-common libopenmpi-dev cmake \
      subversion git libblas-dev liblapack-dev libblas3 liblapack3 libsuitesparse-dev \
      libtool libboost-all-dev splint tcl tcl-dev environment-modules && \
    git clone https://github.com/dealii/candi.git $CANDI_SRC -b master --depth 1 -q && \
    cd $CANDI_SRC && cp $CANDI_DIR/local.cfg . && ./candi.sh --prefix=$CANDI_DIR -j 3 && \
    rm -r $CANDI_DIR/tmp && source $CANDI_DIR/configuration/enable.sh

