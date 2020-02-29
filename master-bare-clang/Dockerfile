FROM teeks99/clang-ubuntu:9
MAINTAINER reza.rastak@gmail.com
ENV DEAL_II_DIR /dealii CC=clang-9 CXX=clang++-9
RUN apt-get update -q && apt-get install -y -q git cmake ninja-build && \
    git clone https://github.com/dealii/dealii.git dealii-src -b master --depth 1 -q && \
    mkdir dealii-src/build && cd dealii-src/build && \
    cmake -GNinja -DDEAL_II_COMPONENT_EXAMPLES=OFF -DCMAKE_INSTALL_PREFIX=/dealii \
    -DCMAKE_BUILD_TYPE=DebugRelease .. && \
    ninja install -j2 && cp summary.log /dealii/summary.log && \
    cd ../ && rm -rf build tests
