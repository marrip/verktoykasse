FROM ubuntu:18.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.17.1-1ubuntu0.7 ca-certificates=20210119~18.04.1 cmake=3.10.2-1ubuntu2.18.04.1 build-essential=12.4ubuntu1 zlib1g-dev=1:1.2.11.dfsg-0ubuntu2 libncurses5-dev=6.1-1ubuntu1.18.04 libncursesw5-dev=6.1-1ubuntu1.18.04 pkg-config=0.29.1-0ubuntu2 libgd-dev=2.2.5-4ubuntu0.4 samtools=1.7-1 && \
    rm -rf /var/lib/apt/lists/*
RUN cpan Statistics::Descriptive GD GD::Graph::histogram
RUN git clone --depth 1 --recursive "https://github.com/genome/breakdancer.git"
WORKDIR /breakdancer
RUN git checkout "$VERSION"
RUN mkdir /breakdancer/build
WORKDIR /breakdancer/build
RUN cmake .. -DCMAKE_BUILD_TYPE=release -DCMAKE_INSTALL_PREFIX=/usr/local
RUN make
RUN make install
ENV PATH=$PATH:/breakdancer/perl
