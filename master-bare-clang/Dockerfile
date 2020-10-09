FROM teeks99/clang-ubuntu:12
LABEL maintainer="reza.rastak@gmail.com"
RUN adduser --disabled-password --gecos '' dealii
RUN apt-get update -q && apt-get install -y -q \
      git \
      cmake \
      ninja-build
ENV DEAL_II_DIR=/dealii CC=clang-12 CXX=clang++-12
RUN DEAL_II_SRC=/home/dealii/dealii-src && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    mkdir $DEAL_II_SRC/build && cd $DEAL_II_SRC/build && \
    cmake -GNinja \
      -D DEAL_II_COMPONENT_EXAMPLES=ON \
      -D CMAKE_BUILD_TYPE=DebugRelease \
      -D DEAL_II_CXX_FLAGS='-stdlib=libc++' \
      -D DEAL_II_LINKER_FLAGS='-stdlib=libc++' \
      -D CMAKE_CXX_STANDARD=17 \
      -D CMAKE_CXX_EXTENSIONS=OFF \
      -D CMAKE_INSTALL_PREFIX=$DEAL_II_DIR \
      -D DEAL_II_ALLOW_AUTODETECTION=OFF \
      .. && \
    ninja install -j3 -v && \
    cd ../../ && \
    rm -rf $DEAL_II_SRC
