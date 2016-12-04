
Dockerfile for Haskell GHC building
-----------------------------------

This is a Dockerfile for building ghc with following condition:
  * OS     : ubuntu 16.04LTS on docker
  * source : ghc 8.0 branch

If you need Debian and Arcanist, please use [Greg's Dockerfile][1].



## How to build

1. ghc building with Dockerfile
  ```
  $ cp Dockerfile_ubuntu16.04_ghc8.0 Dockerfile
  $ docker build -t <YOUR_IMAGE_TAG> .
  ```

2. try your ghc binary
  ```
  $ docker run -it <YOUR_IMAGE_TAG>
  # cd ~/ghc_build/ghc-8.0
  # ./inplace/bin/ghc-stage2 --interactive
  ```


## And more

  3. try validation
  
    If you need trying validation, try following:

  ```
  # cd ~/ghc_build/ghc-8.0
  # ./validate --fast --testsuite-only
   or
  # ./validate
  ```


## References

 * https://ghc.haskell.org/trac/ghc/wiki/Building/Preparation/Linux
 * https://ghc.haskell.org/trac/ghc/wiki/Building/GettingTheSources
 * https://ghc.haskell.org/trac/ghc/wiki/Building/QuickStart
 * https://ghc.haskell.org/trac/ghc/wiki/TestingPatches
 * https://ghc.haskell.org/trac/ghc/wiki/Newcomers

[1]: https://github.com/gregwebs/ghc-docker-dev
