ARG GCC_DOCKER_IMAGE=gcc:10.2
FROM $GCC_DOCKER_IMAGE
LABEL maintainer="reza.rastak@gmail.com"
ARG MPI_PACKAGE_LINK=https://download.open-mpi.org/release/open-mpi/v4.0/openmpi-4.0.5.tar.gz
ARG MPI_VERSION=4.0.5
ENV MPI_DIR=/opt/openmpi
RUN MPI_TAR_FILE=$MPI_DIR/openmpi-$MPI_VERSION.tar.gz && \
    MPI_SRC=$MPI_DIR/openmpi-$MPI_VERSION && \
    mkdir $MPI_DIR && \
    wget --no-verbose --output-document $MPI_TAR_FILE $MPI_PACKAGE_LINK && \
    tar xzvf $MPI_TAR_FILE -C $MPI_DIR && \
    cd $MPI_SRC && \
    ./configure --prefix=$MPI_DIR && \
    make all install && \
    rm -r $MPI_SRC $MPI_TAR_FILE
ENV PATH="${MPI_DIR}/bin:${PATH}" CC=mpicc CXX=mpicxx FC=mpif90 F77=mpif77 MPI_BASE_DIR=$MPI_DIR

