ARG BASE_IMAGE=teeks99/clang-ubuntu:13
FROM $BASE_IMAGE
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get install -y -q \
      curl \
      cmake
ENV DEAL_II_DIR=/opt/dealii CC=clang-$llvmver CXX=clang++-$llvmver
ARG DEAL_II_BUILD_TYPE=Debug
ARG DEAL_II_EXAMPLES=OFF
RUN ( curl -L https://github.com/dealii/dealii/tarball/master | tar xzf - -C /opt/ ) && \
    DEAL_II_SRC="/opt/dealii-dealii*" && DEAL_II_BIN=/opt/dealii-build && \
    cmake \
      -D DEAL_II_COMPONENT_EXAMPLES=$DEAL_II_BUILD_TYPE \
      -D CMAKE_BUILD_TYPE=$DEAL_II_BUILD_TYPE \
      -D DEAL_II_CXX_FLAGS='-stdlib=libc++' \
      -D DEAL_II_LINKER_FLAGS='-stdlib=libc++ -lc++abi' \
      -D CMAKE_CXX_STANDARD=20 \
      -D CMAKE_CXX_EXTENSIONS=OFF \
      -D DEAL_II_ALLOW_AUTODETECTION=OFF \
      -D DEAL_II_WITH_MUPARSER=ON \
      -D DEAL_II_FORCE_BUNDLED_BOOST=ON \
      --install-prefix $DEAL_II_DIR -S $DEAL_II_SRC -B $DEAL_II_BIN && \
    cmake --build $DEAL_II_BIN --parallel 3 --verbose && \
    cmake --install $DEAL_II_BIN && \
    rm -r $DEAL_II_SRC $DEAL_II_BIN
