FROM ubuntu:20.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.25.1-1ubuntu3.2 wget=1.20.3-1ubuntu1 ca-certificates=20210119~20.04.2 bowtie2=2.3.5.1-6build1 libgd-graph-perl=1.54~ds-2&& \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/StevenWingett/FastQ-Screen.git
ENV PATH=$PATH:/FastQ-Screen
