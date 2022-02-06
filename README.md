# dealii-containers

[![](https://img.shields.io/docker/pulls/rrastak/dealii?style=plastic "Docker hub")](https://hub.docker.com/r/rrastak/dealii)
[![Dealii](https://github.com/rezarastak/dealii-containers/workflows/Dealii/badge.svg)](https://github.com/rezarastak/dealii-containers/actions?query=workflow%3ADealii)
[![MPI](https://github.com/rezarastak/dealii-containers/workflows/MPI/badge.svg)](https://github.com/rezarastak/dealii-containers/actions?query=workflow%3AMPI)
[![Trilinos](https://github.com/rezarastak/dealii-containers/workflows/Trilinos/badge.svg)](https://github.com/rezarastak/dealii-containers/actions?query=workflow%3ATrilinos)

Creates docker containers images to use the dealii library.
These images are excellent tools for performing CI and CD in codebases.
You can pull the docker images from the docker hub [repository](https://hub.docker.com/r/rrastak/dealii).
Each container created with these images provides the environment variable `DEAL_II_DIR` which allows any `dealii` code to be compiled using the proper `cmake` configuration.

Three different images are provided here:
 * **dealii:ubuntu-package**: contains the latest official dealii package `libdeal.ii-dev` for the latest Ubuntu LTS.
 * **dealii:ubuntu-package-18**: contains the latest official dealii package `libdeal.ii-dev` backported for Ubuntu 18.04 LTS.
 * **dealii:master-bare-gcc**: is compiled from source using `gcc` with no dependency to external libraries.
 * **dealii:master-bare-clang**: is compiled from source using `clang` with no dependency to external libraries.
 * **trilinos**: This container encapsulates the `Trilinos` library without an installed dealii. It could be used as a base image for compiling dealii.
 * **openmpi**: Encapsulates the openMPI library. It could be used as base image for compiling dealii.

 | Image | Size |
 |---|---|
 |`rrastak/dealii:ubuntu-package`    | ![](https://img.shields.io/docker/image-size/rrastak/dealii/ubuntu-package)|
 |`rrastak/dealii:ubuntu-package-18`    | ![](https://img.shields.io/docker/image-size/rrastak/dealii/ubuntu-package-18)|
 |`rrastak/dealii:master-bare-gcc`   | ![](https://img.shields.io/docker/image-size/rrastak/dealii/master-bare-gcc)|
 |`rrastak/dealii:master-bare-clang` | ![](https://img.shields.io/docker/image-size/rrastak/dealii/master-bare-clang)|
 |`rrastak/trilinos:gcc`   | ![](https://img.shields.io/docker/image-size/rrastak/trilinos/gcc)|
 |`rrastak/trilinos:clang`   | ![](https://img.shields.io/docker/image-size/rrastak/trilinos/clang)|
 |`rrastak/openmpi:gcc`   | ![](https://img.shields.io/docker/image-size/rrastak/openmpi/gcc)|
 |`rrastak/openmpi:clang`   | ![](https://img.shields.io/docker/image-size/rrastak/openmpi/clang)|

