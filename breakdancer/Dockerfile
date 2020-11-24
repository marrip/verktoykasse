FROM ubuntu:18.04
ARG BREAKDANCER_VERSION
RUN apt-get update && \
    apt-get install -y git cmake build-essential zlib1g-dev libncurses5-dev libncursesw5-dev && \
    rm -rf /var/lib/apt/lists/*
RUN git clone --depth 1 --recursive "https://github.com/genome/breakdancer.git" && \
    cd /breakdancer && \
    git checkout "$BREAKDANCER_VERSION"
RUN mkdir /breakdancer/build
WORKDIR /breakdancer/build
RUN cmake .. -DCMAKE_BUILD_TYPE=release -DCMAKE_INSTALL_PREFIX=/usr/local
RUN make
RUN make install
