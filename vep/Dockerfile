FROM ubuntu:16.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.7.4-0ubuntu1.9 ca-certificates=20201027ubuntu0.16.04.1 build-essential=12.1ubuntu2 cpanminus=1.7040-1 libdbd-mysql-perl=4.033-1ubuntu0.1 curl=7.47.0-1ubuntu2.18 unzip=6.0-20ubuntu1.1 zlib1g-dev=1:1.2.8.dfsg-2ubuntu4.3 libbz2-dev=1.0.6-8ubuntu0.2 liblzma-dev=5.1.1alpha+20120614-2ubuntu2 bioperl=1.6.924-3 && \
    rm -rf /var/lib/apt/lists/*
RUN cpanm DBI Try::Tiny
RUN git clone --depth 1 -b $VERSION "https://github.com/Ensembl/ensembl-vep.git"
WORKDIR /ensembl-vep
RUN perl INSTALL.pl
ENV PATH=$PATH:/ensembl-vep
