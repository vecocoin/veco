# Cross-Compiling VECO for Windows (.exe) using Docker & x86_64-w64-mingw32

This setup uses a Docker container with MinGW to build Windows binaries (e.g., `veco-qt.exe` and `veco-cli.exe`) from Linux.

1. Build the Docker image:

`docker build -f docker/Dockerfile.mingw64 -t veco-windows-build .`

2. Run the container & mount your source code:

`docker run -it --rm -v "$PWD":/workspace veco-windows-build`

3. Inside the container, build the dependencies:
```
cd depends
make HOST=x86_64-w64-mingw32
```
You can try `make HOST=x86_64-w64-mingw32 -j$(nproc)` to speed up the process but this may result in errors.

4. Configure and compile
```
cd ..
./autogen.sh
./configure --disable-tests --disable-bench --with-incompatible-bdb --prefix=$(pwd)/depends/x86_64-w64-mingw32
make -j$(nproc)
```

5. Strip the resulting qt binary:

`x86_64-w64-mingw32-strip src/qt/veco-qt.exe`

