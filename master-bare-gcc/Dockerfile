FROM gcc:latest
LABEL maintainer="reza.rastak@gmail.com"
ENV DEAL_II_DIR=/dealii
RUN adduser --disabled-password --gecos '' dealii && \
    apt-get update -q && apt-get upgrade -y -q && \
    apt-get install -y -q git cmake ninja-build && \
    DEAL_II_SRC=/home/dealii/dealii-src && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    mkdir $DEAL_II_SRC/build && cd $DEAL_II_SRC/build && \
    cmake -GNinja -D DEAL_II_COMPONENT_EXAMPLES=ON -D CMAKE_BUILD_TYPE=DebugRelease \
      -D CMAKE_CXX_STANDARD=20 -D CMAKE_CXX_EXTENSIONS=OFF \
      -D CMAKE_INSTALL_PREFIX=$DEAL_II_DIR -D DEAL_II_ALLOW_AUTODETECTION=OFF .. && \
    ninja install -j3 -v && cp summary.log $DEAL_II_DIR/summary.log && \
    cd ../../ && rm -rf $DEAL_II_SRC
