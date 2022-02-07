ARG BASE_IMAGE=teeks99/clang-ubuntu:12
FROM $BASE_IMAGE
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
    DEAL_II_DIN=$DEAL_II_SRC/build && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    cmake -G Ninja \
      -D DEAL_II_COMPONENT_EXAMPLES=$DEAL_II_BUILD_TYPE \
      -D CMAKE_BUILD_TYPE=$DEAL_II_BUILD_TYPE \
      -D DEAL_II_CXX_FLAGS='-stdlib=libc++' \
      -D DEAL_II_LINKER_FLAGS='-stdlib=libc++' \
      -D CMAKE_CXX_STANDARD=20 \
      -D CMAKE_CXX_EXTENSIONS=OFF \
      -D DEAL_II_ALLOW_AUTODETECTION=OFF \
      -D DEAL_II_WITH_MUPARSER=ON \
      -D DEAL_II_FORCE_BUNDLED_BOOST=ON \
      --install-prefix $DEAL_II_DIR -S $DEAL_II_SRC -B $DEAL_II_BIN && \
    cmake --build $DEAL_II_BIN --parallel --verbose && \
    cmake --install $DEAL_II_BIN && \
    rm -rf $DEAL_II_SRC
