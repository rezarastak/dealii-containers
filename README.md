# dealii-containers

[![](https://img.shields.io/docker/pulls/rrastak/dealii?style=plastic "Docker hub")](https://hub.docker.com/r/rrastak/dealii)
[![Docker](https://github.com/rezarastak/dealii-containers/workflows/Docker/badge.svg)](https://github.com/rezarastak/dealii-containers/actions)

Creates docker containers images to use the dealii library.
These images are excellent tools for performing CI and CD in codebases.
You can pull the docker images from the docker hub [repository](https://hub.docker.com/r/rrastak/dealii).
Each container created with these images provides the environment variable `DEAL_II_DIR` which allows any `dealii` code to be compiled using the proper `cmake` configuration.

Three different images are provided here:
 * **ubuntu-package** [![](https://images.microbadger.com/badges/image/rrastak/dealii:ubuntu-package.svg)](https://microbadger.com/images/rrastak/dealii:ubuntu-package "Get your own image badge on microbadger.com") : contains the latest official dealii package `libdeal.ii-dev` for for the latest ubuntu LTS.
 * **master-bare-gcc** [![](https://images.microbadger.com/badges/image/rrastak/dealii:master-bare-gcc.svg)](https://microbadger.com/images/rrastak/dealii:master-bare-gcc "Get your own image badge on microbadger.com") : is compiled from source using `gcc` with no dependency to external libraries.
 * **master-bare-clang** [![](https://images.microbadger.com/badges/image/rrastak/dealii:master-bare-clang.svg)](https://microbadger.com/images/rrastak/dealii:master-bare-clang "Get your own image badge on microbadger.com") : is compiled from source using `clang` with no dependency to external libraries.

