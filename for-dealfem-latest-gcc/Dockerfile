FROM rrastak/trilinos:13.0.0-gcc
LABEL maintainer="reza.rastak@gmail.com"
ENV P4EST_DIR=/opt/p4est
ARG P4EST_PACKAGE_LINK=https://p4est.github.io/release/p4est-2.2.tar.gz
RUN mkdir $P4EST_DIR && \
    P4EST_TAR_FILE_NAME=$(basename $P4EST_PACKAGE_LINK) && \
    P4EST_TAR_PATH=$P4EST_DIR/$P4EST_TAR_FILE_NAME && \
    wget $P4EST_PACKAGE_LINK -O $P4EST_TAR_PATH && \
    tar xzvf $P4EST_TAR_PATH -C $P4EST_DIR && \
    P4EST_SRC=$P4EST_DIR/${P4EST_TAR_FILE_NAME%.tar.gz} && \
    cd $P4EST_SRC && \
    ./configure F77=mpif77 --enable-mpi --enable-shared --disable-vtk-binary --prefix=$P4EST_DIR && \
    make -j10 install && \
    rm -r $P4EST_SRC
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
      -D DEAL_II_WITH_P4EST=ON \
      -D P4EST_DIR=$P4EST_DIR \
      -D DEAL_II_WITH_LAPACK=ON \
      -D DEAL_II_WITH_MUPARSER=ON \
      .. && \
    make -j10 install && \
    cd ../../ && \
    rm -rf $DEAL_II_SRC
