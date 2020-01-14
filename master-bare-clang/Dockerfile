FROM teeks99/clang-ubuntu:9
MAINTAINER reza.rastak@gmail.com
RUN apt-get update -q && apt-get install -y -q git cmake ninja-build && \
    git clone https://github.com/dealii/dealii.git dealii-src -b master --depth 1 -q && \
    mkdir dealii-src/build && cd dealii-src/build && \
    cmake -GNinja -DDEAL_II_COMPONENT_EXAMPLES=OFF -DCMAKE_INSTALL_PREFIX=/dealii \
    -DCMAKE_BUILD_TYPE=DebugRelease .. && \
    ninja install -j3 && cp summary.log /dealii/summary.log && \
    cd ../ && rm -rf build tests
ENV DEAL_II_DIR /dealii
