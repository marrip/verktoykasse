FROM python:2.7.18-buster AS compiler
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.20.1-1.1 ca-certificates=20200601~deb10u2 zlib1g-dev=1:1.2.11.dfsg-1 bzip2=1.0.6-9.2~deb10u1 && \
    rm -rf /var/lib/apt/lists/*
RUN wget "https://github.com/Illumina/strelka/releases/download/v${VERSION}/strelka-${VERSION}.release_src.tar.bz2" && \
    tar -xjf strelka-${VERSION}.release_src.tar.bz2
RUN mkdir /build
WORKDIR /build
RUN /strelka-${VERSION}.release_src/configure --jobs=4 --prefix=/build
RUN make -C /build && make install

FROM python:2.7.18-slim-buster
RUN apt-get update && \
    apt-get install -y --no-install-recommends zlib1g-dev=1:1.2.11.dfsg-1 && \
    rm -rf /var/lib/apt/lists/*
COPY --from=compiler /build/bin /build/bin
COPY --from=compiler /build/bootstrap /build/bootstrap
COPY --from=compiler /build/buildTimeConfigInfo.txt /build/buildTimeConfigInfo.txt
COPY --from=compiler /build/lib /build/lib
COPY --from=compiler /build/libexec /build/libexec
COPY --from=compiler /build/redist /build/redist
RUN true
COPY --from=compiler /build/src/python /build/src/python
RUN true
COPY --from=compiler /build/src/c++ /build/src/c++
ENV PATH=$PATH:/build/bin
