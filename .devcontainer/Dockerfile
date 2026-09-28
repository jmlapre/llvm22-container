FROM debian:trixie-20260918-slim

LABEL maintainer="jmlapre@sandia.gov"

COPY library-scripts/common-debian.sh /tmp/library-scripts/

RUN apt-get update \
    && export DEBIAN_FRONTEND=noninteractive \
    && bash /tmp/library-scripts/common-debian.sh \
    && apt-get --no-install-recommends -y install \
    automake \
    bison \
    build-essential \
    cmake-curses-gui \
    cython3 \
    flex \
    libjansson-dev \
    libkrb5-dev \
    libreadline-dev \
    libssl-dev \
    libtool \
    libltdl-dev \
    locate \
    m4 \
    pkg-config \
    python-is-python3 \
    python3-dev \
    python3-docutils \
    python3-numpy \
    python3-pip \
    python3-venv \
    uuid-dev \
    && rm -rf /var/lib/apt/lists/*

RUN curl -SL https://apt.llvm.org/llvm.sh -o llvm.sh && \
    export DEBIAN_FRONTEND=noninteractive && \
    chmod +x llvm.sh && \
    ./llvm.sh 22 all && \
    rm -rf /var/lib/apt/lists/*

USER vscode
# It's too easy to forget this.  Add it to the Dockerfile.
ENV LDFLAGS="-fuse-ld=lld"
