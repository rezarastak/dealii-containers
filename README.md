# dealii-containers

[![](https://img.shields.io/docker/pulls/rrastak/dealii?style=plastic "Docker hub")](https://hub.docker.com/r/rrastak/dealii)
[![Docker](https://github.com/rezarastak/dealii-containers/workflows/Docker/badge.svg)](https://github.com/rezarastak/dealii-containers/actions)

Creates docker containers images to use the dealii library.
These images are excellent tools for performing CI and CD in codebases.
You can pull the docker images from the docker hub [repository](https://hub.docker.com/r/rrastak/dealii).
Each container created with these images provides the environment variable `DEAL_II_DIR` which allows any `dealii` code to be compiled using the proper `cmake` configuration.

Three different images are provided here:
 * **ubuntu-package**: contains the latest official dealii package `libdeal.ii-dev` for the latest Ubuntu LTS.
 * **ubuntu-package-18**: contains the latest official dealii package `libdeal.ii-dev` for Ubuntu 18.04 LTS.
 * **master-bare-gcc**: is compiled from source using `gcc` with no dependency to external libraries.
 * **master-bare-clang**: is compiled from source using `clang` with no dependency to external libraries.
 * **for-dealfem**: The master-branch build with enough dependencies to allow compiling `dealfem`.

 | Image | Layers | Size |
 |---|---|---|
 |`rrastak/dealii:ubuntu-package` | ![](https://img.shields.io/microbadger/layers/rrastak/dealii/ubuntu-package)|![](https://img.shields.io/microbadger/image-size/rrastak/dealii/ubuntu-package)|
 |`rrastak/dealii:master-bare-gcc` | ![](https://img.shields.io/microbadger/layers/rrastak/dealii/master-bare-gcc)|![](https://img.shields.io/microbadger/image-size/rrastak/dealii/master-bare-gcc)|
 |`rrastak/dealii:master-bare-clang` | ![](https://img.shields.io/microbadger/layers/rrastak/dealii/master-bare-clang)|![](https://img.shields.io/microbadger/image-size/rrastak/dealii/master-bare-clang)|

