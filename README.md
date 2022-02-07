# dealii-containers

[[![GitHub](https://img.shields.io/github/license/rezarastak/dealii-containers)]](https://github.com/rezarastak/dealii-containers)
[![](https://img.shields.io/docker/pulls/rrastak/dealii?style=plastic "Docker hub")](https://hub.docker.com/r/rrastak/dealii)
[![Dealii](https://github.com/rezarastak/dealii-containers/actions/workflows/dealii.yml/badge.svg)](https://github.com/rezarastak/dealii-containers/actions/workflows/dealii.yml)
[![Dealii-ubuntu-package](https://github.com/rezarastak/dealii-containers/actions/workflows/dealii-ubuntu.yml/badge.svg)](https://github.com/rezarastak/dealii-containers/actions/workflows/dealii-ubuntu.yml)
[![openMPI](https://github.com/rezarastak/dealii-containers/actions/workflows/openmpi.yml/badge.svg)](https://github.com/rezarastak/dealii-containers/actions/workflows/openmpi.yml)
[![Trilinos](https://github.com/rezarastak/dealii-containers/actions/workflows/trilinos.yml/badge.svg)](https://github.com/rezarastak/dealii-containers/actions/workflows/trilinos.yml)

The [GitHub repository](https://github.com/rezarastak/dealii-containers) and its associated [Docker Hub repository](https://hub.docker.com/r/rrastak/dealii) provide docker images that can be used to make use of the [deal.II](https://dealii.org) library.
These images are excellent tools for performing CI and CD in codebases.
Each container created with these images provides the environment variable `DEAL_II_DIR` which allows any `dealii` code to be compiled using the proper [`cmake` configuration](https://dealii.org/developer/users/cmake_user.html).

Several different images are provided here:
 * **dealii:ubuntu-package**: contains the latest official dealii package `libdeal.ii-dev` for the latest Ubuntu LTS.
 * **dealii:ubuntu-package-18**: contains the latest official dealii package `libdeal.ii-dev` back-ported for Ubuntu 18.04 LTS.
 * **dealii:gcc**: The latest master branch of `dealii` is compiled from source using `gcc` with no dependency to external libraries.
 * **dealii:clang**: The latest master branch of `dealii` is compiled from source using `clang` with no dependency to external libraries.
 * **trilinos**: This container encapsulates the `Trilinos` library without an installed dealii. It could be used as a base image for compiling dealii.
 * **openmpi**: Encapsulates the openMPI library. It could be used as base image for compiling dealii.

 | Image | Size |
 |---|---|
 |`rrastak/dealii:ubuntu-package` | ![](https://img.shields.io/docker/image-size/rrastak/dealii/ubuntu-package)|
 |`rrastak/dealii:ubuntu-package-18` | ![](https://img.shields.io/docker/image-size/rrastak/dealii/ubuntu-package-18)|
 |`rrastak/dealii:gcc`  | ![](https://img.shields.io/docker/image-size/rrastak/dealii/gcc)|
 |`rrastak/dealii:clang` | ![](https://img.shields.io/docker/image-size/rrastak/dealii/clang)|
 |`rrastak/trilinos:gcc` | ![](https://img.shields.io/docker/image-size/rrastak/trilinos/gcc)|
 |`rrastak/trilinos:clang` | ![](https://img.shields.io/docker/image-size/rrastak/trilinos/clang)|
 |`rrastak/openmpi:gcc` | ![](https://img.shields.io/docker/image-size/rrastak/openmpi/gcc)|
 |`rrastak/openmpi:clang` | ![](https://img.shields.io/docker/image-size/rrastak/openmpi/clang)|

