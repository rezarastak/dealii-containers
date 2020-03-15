# dealii-containers

![Docker](https://github.com/rezarastak/dealii-containers/workflows/Docker/badge.svg)

Creates docker containers images to use the dealii library.
These images are excellent tools for performing CI and CD in codebases.
You can pull the docker images from the docker hub [repository](https://hub.docker.com/r/rrastak/dealii).
Each container created with these images provides the environment variable `DEAL_II_DIR` which allows any `dealii` code to be compiled using the proper `cmake` configuration.

Three different images are provided here:
 * **ubuntu-package**: contains the official dealii package `libdeal.ii-dev` for ubuntu.
 * **master-bare-gcc**: is compiled from source using `gcc` with no dependency to external libraries.
 * **master-bare-clang**: is compiled from source using `clang` with no dependency to external libraries.

