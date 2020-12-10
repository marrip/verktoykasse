FROM ubuntu:16.04 AS compiler
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.7.4-0ubuntu1.9 ca-certificates=20201027ubuntu0.16.04.1 wget=1.17.1-1ubuntu1.5 libncurses5-dev=6.0+20160213-1ubuntu1 zlib1g-dev=1:1.2.8.dfsg-2ubuntu4.3 build-essential=12.1ubuntu2
RUN wget "https://github.com/samtools/samtools/releases/download/1.2/samtools-1.2.tar.bz2" && \
    tar -xvjf samtools-1.2.tar.bz2
WORKDIR /samtools-1.2
RUN make && \
    make install
WORKDIR /
RUN git clone --depth 1 -b $VERSION https://github.com/genome/pindel.git
WORKDIR /pindel
RUN ./INSTALL /samtools-1.2/htslib-1.2.1

FROM ubuntu:16.04
RUN apt-get update && \
    apt-get install -y --no-install-recommends libgomp1=5.4.0-6ubuntu1~16.04.12 && \
    rm -rf /var/lib/apt/lists/*
COPY --from=compiler /pindel/pindel /usr/local/bin/pindel
COPY --from=compiler /pindel/pindel2vcf /usr/local/bin/pindel2vcf
