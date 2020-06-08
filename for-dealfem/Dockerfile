FROM ubuntu:latest
LABEL maintainer="reza.rastak@gmail.com"
ENV DEAL_II_DIR=/opt/dealii DEAL_II_SRC=/opt/dealii-src
RUN adduser --disabled-password --gecos '' dealii && \
    apt-get update -q && apt-get upgrade -y -q && \
    TZ="America/Los_Angeles" DEBIAN_FRONTEND="noninteractive" \
      apt-get install -y -q build-essential git cmake ninja-build \
      libarpack2-dev libassimp-dev libboost-iostreams-dev libboost-serialization-dev \
      libboost-system-dev libboost-thread-dev libbz2-dev libdeal.ii-9.1.1 libgmsh-dev \
      libgsl-dev libhdf5-dev libhdf5-mpi-dev liblapack-dev libmuparser-dev \
      libnetcdf-cxx-legacy-dev libnetcdf-dev libp4est-dev \
      libscalapack-mpi-dev libsuitesparse-dev libsundials-dev libtbb-dev mpi-default-dev \
      petsc-dev slepc-dev trilinos-all-dev zlib1g-dev && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    mkdir $DEAL_II_SRC/build && cd $DEAL_II_SRC/build && \
    cmake -GNinja -D DEAL_II_COMPONENT_EXAMPLES=ON -D CMAKE_BUILD_TYPE=DebugRelease \
      -D CMAKE_INSTALL_PREFIX=$DEAL_II_DIR -D DEAL_II_ALLOW_AUTODETECTION=OFF \
      -D DEAL_II_WITH_MPI=ON -D DEAL_II_WITH_TRILINOS=ON \
      -D DEAL_II_WITH_P4EST=ON -D DEAL_II_WITH_LAPACK=ON -D DEAL_II_WITH_MUPARSER=ON .. && \
    ninja install -j3 -v && cp summary.log $DEAL_II_DIR/summary.log && \
    cd ../ && rm -rf build tests
