FROM teeks99/clang-ubuntu:9
LABEL maintainer="reza.rastak@gmail.com"
ENV DEAL_II_DIR=/dealii DEAL_II_SRC=/home/dealii/dealii-src CC=clang-9 CXX=clang++-9
RUN adduser --disabled-password --gecos '' dealii && \
    apt-get update -q && apt-get install -y -q git cmake ninja-build && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    mkdir $DEAL_II_SRC/build && cd $DEAL_II_SRC/build && \
    cmake -GNinja -DDEAL_II_COMPONENT_EXAMPLES=OFF -DCMAKE_BUILD_TYPE=DebugRelease \
      -DCMAKE_INSTALL_PREFIX=$DEAL_II_DIR .. && \
    ninja install -j2 -v && cp summary.log $DEAL_II_DIR/summary.log && \
    cd ../ && rm -rf build tests && \
    chown -R dealii $DEAL_II_SRC
