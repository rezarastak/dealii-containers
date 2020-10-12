FROM rrastak/trilinos:13.0.0-gcc
LABEL maintainer="reza.rastak@gmail.com"
ENV DEAL_II_DIR=/opt/dealii
RUN DEAL_II_SRC=/opt/dealii-src && \
    git clone https://github.com/dealii/dealii.git $DEAL_II_SRC -b master --depth 1 -q && \
    mkdir $DEAL_II_SRC/build && cd $DEAL_II_SRC/build && \
    cmake \
      -D CMAKE_BUILD_TYPE=Debug \
      -D CMAKE_CXX_STANDARD=20 \
      -D CMAKE_CXX_EXTENSIONS=OFF \
      -D CMAKE_INSTALL_PREFIX=$DEAL_II_DIR \
      -D DEAL_II_ALLOW_AUTODETECTION=OFF \
      -D DEAL_II_WITH_MPI=ON \
      -D DEAL_II_WITH_TRILINOS=ON \
      -D DEAL_II_WITH_P4EST=OFF \
      -D DEAL_II_WITH_LAPACK=ON \
      -D DEAL_II_WITH_MUPARSER=ON \
      .. && \
    make -j3 install && \
    cd ../../ && \
    rm -rf $DEAL_II_SRC
