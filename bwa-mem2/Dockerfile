FROM ubuntu:18.04
ARG BWAMEM2_VERSION
RUN apt-get update && \
    apt-get install -y wget && \
    rm -rf /var/lib/apt/lists/*
RUN wget "https://github.com/bwa-mem2/bwa-mem2/releases/download/v"$BWAMEM2_VERSION"/bwa-mem2-"$BWAMEM2_VERSION"_x64-linux.tar.bz2" && \
    tar jxf bwa-mem2-"$BWAMEM2_VERSION"_x64-linux.tar.bz2 && \
    rm bwa-mem2-"$BWAMEM2_VERSION"_x64-linux.tar.bz2
ENV PATH=$PATH:/bwa-mem2-"$BWAMEM2_VERSION"_x64-linux
