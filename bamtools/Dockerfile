FROM ubuntu:18.04 AS compiler
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.17.1-1ubuntu0.7 ca-certificates=20201027ubuntu0.18.04.1 build-essential=12.4ubuntu1 cmake=3.10.2-1ubuntu2.18.04.1 libjsoncpp-dev=1.7.4-3 zlib1g-dev=1:1.2.11.dfsg-0ubuntu2 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION git://github.com/pezmaster31/bamtools.git
WORKDIR /bamtools/build
RUN cmake -DCMAKE_INSTALL_PREFIX=/bamtools/build ..
RUN make
RUN make install

FROM ubuntu:18.04
COPY --from=compiler /bamtools/build/bin/bamtools /usr/local/bin/
