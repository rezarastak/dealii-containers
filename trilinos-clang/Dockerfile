ARG BASE_IMAGE=rrastak/openmpi:clang
FROM $BASE_IMAGE
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get install -y -q \
      cmake \
      libblas-dev \
      liblapack-dev
ARG TRILINOS_PACKAGE_LINK=https://github.com/trilinos/Trilinos/archive/refs/tags/trilinos-release-13-0-1.tar.gz
ARG TRILINOS_DIR=/opt/trilinos
RUN TRILINOS_TAR_NAME=$(basename $TRILINOS_PACKAGE_LINK) && \
    TRILINOS_TAR_PATH=$TRILINOS_DIR/$TRILINOS_TAR_NAME && \
    echo preparing tar file $TRILINOS_TAR_PATH && \
    mkdir $TRILINOS_DIR && \
    wget --no-verbose --output-document $TRILINOS_TAR_PATH $TRILINOS_PACKAGE_LINK && \
    TRILINOS_SRC=$TRILINOS_DIR/Trilinos-${TRILINOS_TAR_NAME%.tar.gz} && \
    echo extracting tar file into $TRILINOS_SRC && \
    tar xzvf $TRILINOS_TAR_PATH -C $TRILINOS_DIR && \
    TRILINOS_BUILD=$TRILINOS_SRC/build && \
    cmake \
      -D Trilinos_ENABLE_Fortran=OFF \
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
      --install-prefix $TRILINOS_DIR -S $TRILINOS_SRC -B $TRILINOS_BUILD && \
    cmake --build $TRILINOS_BUILD --parallel 3 --verbose && \
    cmake --install $TRILINOS_BUILD && \
    rm -r $TRILINOS_SRC $TRILINOS_TAR_PATH
