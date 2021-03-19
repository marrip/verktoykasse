FROM ubuntu:18.04 AS compiler
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.17.1-1ubuntu0.8  ca-certificates=20210119~18.04.1 build-essential=12.4ubuntu1 autoconf=2.69-11 zlib1g-dev=1:1.2.11.dfsg-0ubuntu2 libbz2-dev=1.0.6-8.1ubuntu0.2 liblzma-dev=5.2.2-1.3 libboost-all-dev=1.65.1.0ubuntu1 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION --recursive https://github.com/dellytools/delly.git
WORKDIR /delly
RUN make STATIC=1 all && \
    make install
#
FROM ubuntu:18.04
COPY --from=compiler /delly/src/delly /usr/local/bin/
