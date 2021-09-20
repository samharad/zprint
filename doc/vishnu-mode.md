### Vishnu Mode

- Adds support for rama
- Building release binaries
  - Install GraalVM. You may use `sdkman` if you have it. https://www.graalvm.org/downloads/#
  - Build for mac (assumes Graal (i.e. native-image) is already on the path):
    - `lein clean && lein uberjar` 
    - `./build.zprintm "" target/zprint-filter-1.3.0-vishnu-mode zprintm-1.3.0-vishnu-mode`
  - Build for linux
    - Requires docker
    - `./build.zprintl "22" "1.3.0-vishnu-mode"`
    - NOTE: I could not get this working with graal versions 20, 21 or 22. 20 and 21 hang during
      compilation; 22 eventually reports a deadlock.