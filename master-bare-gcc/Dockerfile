FROM gcc:latest
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get install -y -q \
      git \
      cmake \
      ninja-build
ENV DEAL_II_DIR=/opt/dealii
RUN DEAL_II_SRC=/opt/dealii-src && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    mkdir $DEAL_II_SRC/build && cd $DEAL_II_SRC/build && \
    cmake -GNinja \
      -D DEAL_II_COMPONENT_EXAMPLES=ON \
      -D CMAKE_BUILD_TYPE=DebugRelease \
      -D CMAKE_CXX_STANDARD=20 \
      -D CMAKE_CXX_EXTENSIONS=OFF \
      -D CMAKE_INSTALL_PREFIX=$DEAL_II_DIR \
      -D DEAL_II_ALLOW_AUTODETECTION=OFF \
      .. && \
    ninja install -j3 -v && \
    cd ../../ && \
    rm -rf $DEAL_II_SRC
