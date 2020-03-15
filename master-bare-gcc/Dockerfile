FROM gcc:9.2
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get install -q -y cmake ninja-build && \
    git clone https://github.com/dealii/dealii.git dealii-src -b master --depth 1 -q && \
    mkdir dealii-src/build && cd dealii-src/build && \
    cmake -GNinja -DDEAL_II_COMPONENT_EXAMPLES=OFF -DCMAKE_INSTALL_PREFIX=/dealii \
    -DCMAKE_BUILD_TYPE=DebugRelease .. && \
    ninja install -j2 && cp summary.log /dealii/summary.log && \
    cd ../ && rm -rf build tests
ENV DEAL_II_DIR /dealii
