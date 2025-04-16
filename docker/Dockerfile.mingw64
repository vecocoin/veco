FROM debian:bookworm

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y \
    build-essential \
    g++ \
    mingw-w64 \
    gcc-mingw-w64 \
    g++-mingw-w64 \
    g++-mingw-w64-x86-64 \
    binutils-mingw-w64-x86-64 \
    gcc-mingw-w64-x86-64 \
    wine \
    git \
    pkg-config \
    automake \
    autoconf \
    libtool \
    curl \
    ca-certificates \
    zip \
    unzip \
    python3 \
    python3-pip \
    vim \
    nano \
    file \
    dos2unix \
    cmake \
    qt5-qmake \
    qtbase5-dev-tools \
    qttools5-dev-tools

# Set POSIX threading model as default for x86_64-w64-mingw32
RUN update-alternatives --set x86_64-w64-mingw32-g++ /usr/bin/x86_64-w64-mingw32-g++-posix && \
    update-alternatives --set x86_64-w64-mingw32-gcc /usr/bin/x86_64-w64-mingw32-gcc-posix

# Optional: Set up working directory
WORKDIR /workspace

CMD ["/bin/bash"]


