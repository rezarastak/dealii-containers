FROM rrastak/mpi:openmpi-4.0.5-gcc
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get install -y -q \
      cmake \
      libblas-dev \
      liblapack-dev
ARG TRILINOS_PACKAGE_LINK
ARG TRILINOS_DIR=/opt/trilinos
RUN TRILINOS_TAR_NAME=$(basename $TRILINOS_PACKAGE_LINK) && \
    TRILINOS_TAR_PATH=$TRILINOS_DIR/TRILINOS_TAR_NAME && \
    echo preparing tar file $TRILINOS_TAR_PATH && \
    mkdir $TRILINOS_DIR && \
    wget $TRILINOS_PACKAGE_LINK -O $TRILINOS_TAR_PATH && \
    TRILINOS_SRC=$TRILINOS_DIR/Trilinos-${TRILINOS_TAR_NAME%.tar.gz} && \
    echo extracting tar file into $TRILINOS_SRC && \
    tar xzvf $TRILINOS_TAR_PATH -C $TRILINOS_DIR && \
    TRILINOS_BUILD=$TRILINOS_SRC/build && \
    mkdir $TRILINOS_BUILD && cd $TRILINOS_BUILD && \
    cmake \
      -D TPL_ENABLE_MPI=ON \
      -D MPI_BASE_DIR=$MPI_DIR \
      -D Trilinos_ENABLE_Amesos=ON \
      -D Trilinos_ENABLE_AztecOO=ON \
      -D Trilinos_ENABLE_Epetra=ON \
      -D Trilinos_ENABLE_Ifpack=ON \
      -D Trilinos_ENABLE_ML=ON \
      -D Trilinos_ENABLE_Teuchos=ON \
      -D Trilinos_ENABLE_ALL_OPTIONAL_PACKAGES=OFF \
      -D BUILD_SHARED_LIBS=ON \
      -D CMAKE_CXX_STANDARD=20 \
      -D CMAKE_CXX_EXTENSIONS=OFF \
      -D CMAKE_INSTALL_PREFIX=$TRILINOS_DIR \
      .. && \
    make -j3 install && \
    cd ../../ && \
    rm -r $TRILINOS_SRC $TRILINOS_TAR_PATH
