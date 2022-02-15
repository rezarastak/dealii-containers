ARG BASE_IMAGE=teeks99/clang-ubuntu:13
FROM $BASE_IMAGE
LABEL maintainer="reza.rastak@gmail.com"
RUN apt-get update -q && apt-get install -y -q \
    wget
ARG MPI_PACKAGE_LINK=https://download.open-mpi.org/release/open-mpi/v4.1/openmpi-4.1.2.tar.gz
ARG MPI_VERSION=4.1.2
ENV MPI_DIR=/opt/openmpi
RUN MPI_TAR_FILE=$MPI_DIR/openmpi-$MPI_VERSION.tar.gz && \
    MPI_SRC=$MPI_DIR/openmpi-$MPI_VERSION && \
    mkdir $MPI_DIR && \
    wget --no-verbose --output-document $MPI_TAR_FILE $MPI_PACKAGE_LINK && \
    tar xzvf $MPI_TAR_FILE -C $MPI_DIR && \
    cd $MPI_SRC && \
    ./configure CC=clang-13 CXX=clang++-13 --prefix=$MPI_DIR && \
    make all install && \
    rm -r $MPI_SRC $MPI_TAR_FILE
ENV PATH="${MPI_DIR}/bin:${PATH}" CC=mpicc CXX=mpicxx FC=mpif90 F77=mpif77 MPI_BASE_DIR=$MPI_DIR
