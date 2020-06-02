FROM teeks99/clang-ubuntu:9
LABEL maintainer="reza.rastak@gmail.com"
ENV CANDI_DIR=/candi CANDI_SRC=/candi-src CC=clang-9 CXX=clang++-9
COPY local.cfg $CANDI_SRC
RUN adduser --disabled-password --gecos '' dealii && \
    apt-get update -q && apt-get upgrade -y -q && \
    apt-get install -y -q build-essential lsb-release wget automake autoconf \
    gfortran openmpi-bin openmpi-common libopenmpi-dev cmake subversion git \
    libblas-dev liblapack-dev libblas3 liblapack3 libsuitesparse-dev libtool \
    libboost-all-dev splint tcl tcl-dev environment-modules qt4-dev-tools && \
    git clone https://github.com/dealii/candi.git $CANDI_SRC -b master --depth 1 -q && \
    cd $CANDI_SRC && ./candi && rm -r $CANDI_DIR/tmp

