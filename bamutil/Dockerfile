FROM ubuntu:18.04 AS compiler
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.17.1-1ubuntu0.8 ca-certificates=20210119~18.04.1 build-essential=12.4ubuntu1 zlib1g-dev=1:1.2.11.dfsg-0ubuntu2 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/statgen/bamUtil.git
WORKDIR /bamUtil
RUN make cloneLib
RUN make

FROM ubuntu:18.04
COPY --from=compiler /bamUtil/bin/bam /usr/local/bin/
