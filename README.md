
Dockerfile for Haskell GHC building
-----------------------------------

This is a Dockerfile for building ghc with following condition:
  * OS     : ubuntu 16.04LTS or 18.04LTS on docker
  * source : ghc 8.0, 8.2, 8.4, 8.6, 8.8, 8.10 or master branch

If you need Debian and Arcanist, please use [Greg's Dockerfile][1].

Let's get familiar with ghc building and validating :)


## How to build

1. ghc building with Dockerfile
  ```
  $ cp Dockerfile_ubuntu1X.04_ghc8.X Dockerfile
  $ docker build -t <YOUR_IMAGE_TAG> .
  ```
  Please wait for a few hours...

2. execution of your ghc binary
  ```
  $ docker run -it <YOUR_IMAGE_TAG>
  # cd ~/ghc_build/ghc-8.X
  # ./inplace/bin/ghc-stage2 --interactive
  ```


## How to re-build

1. edit source files
  ```
  $ docker run -it <YOUR_IMAGE_TAG>
  # cd ~/ghc_build/ghc-8.X
  # vi <YOUR_FILES>
  ```

2. re-build
  ```
  $ docker run -it <YOUR_IMAGE_TAG>
  # cd ~/ghc_build/ghc-8.X
  # ./boot
  # ./configure
  # make -j 8      
  ```


## How to validate

  If you need trying validation, try following:

  1. validation

  ```
  $ docker run -it <YOUR_IMAGE_TAG>
  # cd ~/ghc_build/ghc-8.X
  # THREADS=8 ./validate
   or
  # ./validate --fast --testsuite-only
  ```

  2. run a indivisual test if you need
  ```
  # cd ~/ghc_build/ghc-8.X/testsuite/tests/<TEST_DIRECORY>
  # make TEST=Txxxx
  ```


## References

 * https://gitlab.haskell.org/ghc/ghc/-/wikis/building/preparation/linux
 * https://gitlab.haskell.org/ghc/ghc/-/wikis/building/getting-the-sources
 * https://gitlab.haskell.org/ghc/ghc/-/wikis/building/quick-start
 * https://gitlab.haskell.org/ghc/ghc/-/wikis/testing-patches
 * https://gitlab.haskell.org/ghc/ghc/-/wikis/building/running-tests/running
 * https://gitlab.haskell.org/ghc/ghc/-/wikis/contributing#newcomers-to-ghc

[1]: https://github.com/gregwebs/ghc-docker-dev
