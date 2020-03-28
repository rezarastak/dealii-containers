FROM gcc:9.2
LABEL maintainer="reza.rastak@gmail.com"
RUN adduser --disabled-password --gecos '' dealii && \
    apt-get update -q && apt-get install -y -q git cmake ninja-build
USER dealii
WORKDIR /home/dealii
RUN git clone https://github.com/dealii/dealii.git dealii-src -b master --depth 1 -q && \
    mkdir dealii-src/build && cd dealii-src/build && \
    cmake -GNinja -DDEAL_II_COMPONENT_EXAMPLES=OFF -DCMAKE_BUILD_TYPE=DebugRelease \
      -DCMAKE_INSTALL_PREFIX=/home/dealii/dealii .. && \
    ninja install -j2 && cp summary.log /home/dealii/dealii/summary.log && \
    cd ../ && rm -rf build tests
ENV USER=dealii DEAL_II_DIR=/home/dealii/dealii
