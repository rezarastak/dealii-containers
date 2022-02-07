ARG BASE_IMAGE=gcc:latest
FROM $BASE_IMAGE
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get install -y -q \
      git \
      cmake \
      ninja-build
ENV DEAL_II_DIR=/opt/dealii
ARG DEAL_II_BUILD_TYPE=DebugRelease
ARG DEAL_II_EXAMPLES=OFF
RUN DEAL_II_SRC=/opt/dealii-src && DEAL_II_BIN=$DEAL_II_SRC/build && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    cmake -G Ninja \
      -D DEAL_II_COMPONENT_EXAMPLES=$DEAL_II_EXAMPLES \
      -D CMAKE_BUILD_TYPE=$DEAL_II_BUILD_TYPE \
      -D CMAKE_CXX_STANDARD=20 \
      -D CMAKE_CXX_EXTENSIONS=OFF \
      -D DEAL_II_ALLOW_AUTODETECTION=OFF \
      --install-prefix $DEAL_II_DIR -S $DEAL_II_SRC -B $DEAL_II_BIN && \
    cmake --build $DEAL_II_BIN --parallel --verbose && \
    cmake --install $DEAL_II_BIN && \
    rm -rf $DEAL_II_SRC
