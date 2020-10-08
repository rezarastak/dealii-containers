FROM gcc:latest
LABEL maintainer="reza.rastak@gmail.com"
ARG MPI_PACKAGE_LINK
ARG MPI_VERSION
ENV MPI_DIR=/openmpi
RUN MPI_TAR_FILE=$MPI_DIR/openmpi-$MPI_VERSION.tar.gz && \
    MPI_SRC=$MPI_DIR/openmpi-$MPI_VERSION && \
    mkdir $MPI_DIR && \
    wget $MPI_PACKAGE_LINK -O $MPI_TAR_FILE && \
    tar xzvf $MPI_TAR_FILE -C $MPI_DIR && \
    cd $MPI_SRC && \
    ./configure --prefix=$MPI_DIR && \
    make -j4 all install && \
    rm -r $MPI_SRC $MPI_TAR_FILE
ENV PATH="${MPI_DIR}/bin:${PATH}" CC=mpicc CXX=mpicxx FC=mpif90 F77=mpi77

