FROM python:2.7.18-buster AS compiler
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.20.1-2+deb10u3 ca-certificates=20200601~deb10u1 zlib1g-dev=1:1.2.11.dfsg-1 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone --depth 1 -b $VERSION "https://github.com/Illumina/manta.git"
RUN mkdir /build
WORKDIR /build
RUN /manta/configure --jobs=4 --prefix=/build
RUN make -C /build && make install

FROM python:2.7.18-buster
RUN apt-get update && \
    apt-get install -y --no-install-recommends zlib1g-dev=1:1.2.11.dfsg-1 && \
    rm -rf /var/lib/apt/lists/*
COPY --from=compiler /build/bin /build/bin
COPY --from=compiler /build/bootstrap /build/bootstrap
COPY --from=compiler /build/buildTimeConfigInfo.txt /build/buildTimeConfigInfo.txt
COPY --from=compiler /build/lib /build/lib
COPY --from=compiler /build/libexec /build/libexec
COPY --from=compiler /build/redist /build/redist
COPY --from=compiler /build/lib /build/lib
RUN true
COPY --from=compiler /build/src/python /build/src/python
RUN true
COPY --from=compiler /build/src/c++ /build/src/c++
ENV PATH=$PATH:/build/bin
