FROM ubuntu:20.04 AS compiler
ARG VERSION
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.25.1-1ubuntu3.1 ca-certificates=20210119~20.04.1 build-essential=12.8ubuntu1.1 cmake=3.16.3-1ubuntu1 libjsoncpp-dev=1.7.4-3.1ubuntu2 zlib1g-dev=1:1.2.11.dfsg-2ubuntu1.2 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION git://github.com/pezmaster31/bamtools.git
WORKDIR /bamtools/build
RUN cmake -DCMAKE_INSTALL_PREFIX=/bamtools/build ..
RUN make
RUN make install

FROM ubuntu:20.04
COPY --from=compiler /bamtools/build/bin/bamtools /usr/local/bin/
