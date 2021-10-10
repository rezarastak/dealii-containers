ARG CLANG_DOCKER_IMAGE=teeks99/clang-ubuntu:12
FROM $CLANG_DOCKER_IMAGE
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get install -y -q \
      git \
      cmake \
      ninja-build \
      libunwind-dev
ENV DEAL_II_DIR=/opt/dealii CC=clang-12 CXX=clang++-12
ARG DEAL_II_BUILD_TYPE=DebugRelease
ARG DEAL_II_EXAMPLES=OFF
RUN DEAL_II_SRC=/opt/dealii-src && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    mkdir $DEAL_II_SRC/build && cd $DEAL_II_SRC/build && \
    cmake -GNinja \
      -D DEAL_II_COMPONENT_EXAMPLES=$DEAL_II_BUILD_TYPE \
      -D CMAKE_BUILD_TYPE=$DEAL_II_BUILD_TYPE \
      -D DEAL_II_CXX_FLAGS='-stdlib=libc++' \
      -D DEAL_II_LINKER_FLAGS='-stdlib=libc++' \
      -D CMAKE_CXX_STANDARD=20 \
      -D CMAKE_CXX_EXTENSIONS=OFF \
      -D CMAKE_INSTALL_PREFIX=$DEAL_II_DIR \
      -D DEAL_II_ALLOW_AUTODETECTION=OFF \
      -D DEAL_II_WITH_MUPARSER=ON \
      -D DEAL_II_FORCE_BUNDLED_BOOST=ON \
      .. && \
    ninja install -j3 -v && \
    cd ../../ && \
    rm -rf $DEAL_II_SRC
