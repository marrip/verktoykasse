FROM ubuntu:20.04 AS builder
ARG VERSION
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.25.1-1ubuntu3.1 ca-certificates=20210119~20.04.1 autoconf=2.69-11.1 gawk=1:5.0.1+dfsg-1 build-essential=12.8ubuntu1.1 pkg-config=0.29.1-0ubuntu4 libtool=2.4.6-14 automake=1:1.16.1-4ubuntu6 zlib1g-dev=1:1.2.11.dfsg-2ubuntu1.2 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/vcftools/vcftools.git
WORKDIR /vcftools
RUN ./autogen.sh && \
    ./configure
RUN make && \
    make install

FROM ubuntu:20.04
COPY --from=builder /usr/local/bin/* /usr/local/bin/
