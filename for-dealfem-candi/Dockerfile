FROM ubuntu:latest
LABEL maintainer="reza.rastak@gmail.com"
RUN adduser --disabled-password --gecos '' dealii
RUN apt-get update -q && \
    TZ="America/Los_Angeles" DEBIAN_FRONTEND="noninteractive" apt-get install -y -q \
      build-essential \
      python \
      bc \
      ninja-build \
      lsb-release \
      wget \
      numdiff \
      automake \
      autoconf \
      gfortran \
      mpi-default-dev \
      cmake \
      subversion \
      git \
      libblas-dev \
      liblapack-dev \
      libblas3 \
      liblapack3 \
      libsuitesparse-dev \
      libtool \
      libboost-all-dev \
      splint \
      tcl \
      tcl-dev
ENV CANDI_DIR=/candi CANDI_SRC=/candi-src
COPY local.cfg $CANDI_DIR/
RUN git clone https://github.com/dealii/candi.git $CANDI_SRC -b master --depth 1 -q && \
    cd $CANDI_SRC && \
    cp $CANDI_DIR/local.cfg . && \
    ./candi.sh --prefix=$CANDI_DIR -j 2 && \
    rm -r $CANDI_DIR/tmp
ENV DEAL_II_DIR=/candi/deal.II-master
