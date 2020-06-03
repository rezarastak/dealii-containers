FROM ubuntu:latest
LABEL maintainer="reza.rastak@gmail.com"
ENV DEAL_II_DIR=/opt/dealii DEAL_II_SRC=/opt/dealii-src
RUN apt-get update -q && apt-get upgrade -y -q && \
    TZ="America/Los_Angeles" DEBIAN_FRONTEND="noninteractive" \
      apt-get install -y -q git cmake ninja-build liblapack-dev libmuparser-dev \
      libp4est-dev trilinos-all-dev && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    mkdir $DEAL_II_SRC/build && cd $DEAL_II_SRC/build && \
    cmake -GNinja -D DEAL_II_COMPONENT_EXAMPLES=OFF -D CMAKE_BUILD_TYPE=DebugRelease \
      -D CMAKE_INSTALL_PREFIX=$DEAL_II_DIR -D DEAL_II_ALLOW_AUTODETECTION=OFF \
      -D DEAL_II_WITH_MPI=ON -D DEAL_II_WITH_TRILINOS=ON -D DEAL_II_WITH_THREADS=ON \
      -D DEAL_II_WITH_P4EST=ON -D DEAL_II_WITH_LAPACK=ON -D DEAL_II_WITH_MUPARSER=ON .. && \
    ninja install -j3 -v && cp summary.log $DEAL_II_DIR/summary.log && \
    cd ../ && rm -rf build tests
