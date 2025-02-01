# dawn-build

This repository includes the compiled library for SDL3, compatible with both Windows and macOS.

## Steps to build SDL3

```shell
# Change to the directory where you want to create the code repository
$ git clone https://github.com/libsdl-org/SDL.git
Cloning into 'SDL'...
```

Git will create the repository within a directory named `SDL`. Navigate into this directory and configure the project.

### Build and install SDL3 with CMake

#### Debug Build
```shell
$ cd SDL
$ cmake -S . -B out/Debug -DSDL_SHARED=ON -DSDL_TEST_LIBRARY=OFF -DSDL_TESTS=OFF -DSDL_DISABLE_INSTALL=OFF -DSDL_DISABLE_INSTALL_DOCS=ON -DSDL_INSTALL_TESTS=OFF -DCMAKE_BUILD_TYPE=Debug
...
-- Configuring done (34.9s)
-- Generating done (0.8s)
-- Build files have been written to: ${PWD}/out/Debug
```

Now you can build SDL3:

```shell
$ cmake --build out/Debug --config debug
```

Once you have built the SDL3 library, install it with `cmake`

```shell
$ cmake --install out/Debug --prefix install/Debug --config Debug
```

This installs Dawn from the `out/Debug` build tree into `install/Debug`.

#### Release Build
```shell
$ cd SDL
$ cmake -S . -B out/Release -DSDL_SHARED=ON -DSDL_TEST_LIBRARY=OFF -DSDL_TESTS=OFF -DSDL_DISABLE_INSTALL=OFF -DSDL_DISABLE_INSTALL_DOCS=ON -DSDL_INSTALL_TESTS=OFF -DCMAKE_BUILD_TYPE=Release
...
-- Configuring done (34.9s)
-- Generating done (0.8s)
-- Build files have been written to: ${PWD}/out/Release
```

Now you can build SDL3:

```shell
$ cmake --build out/Release --config Release
```

Once you have built the Dawn library, install it with `cmake`

```shell
$ cmake --install out/Release --prefix install/Release --config Release
```

This installs SDL3 from the `out/Release` build tree into `install/Release`.
