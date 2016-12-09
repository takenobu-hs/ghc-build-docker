
Dockerfile for Haskell GHC building
-----------------------------------

This is a Dockerfile for building ghc with following condition:
  * OS     : ubuntu 16.04LTS on docker
  * source : ghc 8.0 branch

If you need Debian and Arcanist, please use [Greg's Dockerfile][1].

Let's get familiar with ghc building and validating :)


## How to build

1. ghc building with Dockerfile
  ```
  $ cp Dockerfile_ubuntu16.04_ghc8.0 Dockerfile
  $ docker build -t <YOUR_IMAGE_TAG> .
  ```
  Please wait for a few hours...

2. execution of your ghc binary
  ```
  $ docker run -it <YOUR_IMAGE_TAG>
  # cd ~/ghc_build/ghc-8.0
  # ./inplace/bin/ghc-stage2 --interactive
  ```


## How to re-build

1. edit source files
  ```
  $ docker run -it <YOUR_IMAGE_TAG>
  # cd ~/ghc_build/ghc-8.0
  # vi <YOUR_FILES>
  ```

2. re-build
  ```
  $ docker run -it <YOUR_IMAGE_TAG>
  # cd ~/ghc_build/ghc-8.0
  # ./boot
  # ./configure
  # make -j 8      
  ```


## How to validate

  If you need trying validation, try following:

  1. validation

  ```
  $ docker run -it <YOUR_IMAGE_TAG>
  # cd ~/ghc_build/ghc-8.0
  # THREADS=8 ./validate
   or
  # ./validate --fast --testsuite-only
  ```

  2. run a indivisual test if you need
  ```
  # cd ~/ghc_build/ghc-8.0/testsuite/tests/<TEST_DIRECORY>
  # make TEST=Txxxx
  ```


## References

 * https://ghc.haskell.org/trac/ghc/wiki/Building/Preparation/Linux
 * https://ghc.haskell.org/trac/ghc/wiki/Building/GettingTheSources
 * https://ghc.haskell.org/trac/ghc/wiki/Building/QuickStart
 * https://ghc.haskell.org/trac/ghc/wiki/TestingPatches
 * https://ghc.haskell.org/trac/ghc/wiki/Building/RunningTests/Running
 * https://ghc.haskell.org/trac/ghc/wiki/Newcomers

[1]: https://github.com/gregwebs/ghc-docker-dev
