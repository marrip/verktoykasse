FROM ubuntu:18.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.19.4-1ubuntu2.2 ca-certificates=20201027ubuntu0.18.04.1 build-essential=12.4ubuntu1 zlib1g-dev=1:1.2.11.dfsg-0ubuntu2 && \
    rm -rf /var/lib/apt/lists/*
RUN wget "https://github.com/lh3/bwa/releases/download/v${VERSION}/bwa-${VERSION}.tar.bz2" && \
    tar jxf bwa-${VERSION}.tar.bz2 && \
    rm bwa-${VERSION}.tar.bz2
WORKDIR /bwa-${VERSION}
RUN make
ENV PATH=$PATH:/bwa-${VERSION}
