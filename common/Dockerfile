FROM ubuntu:18.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends bedtools=2.26.0+dfsg-5 samtools=1.7-1 bcftools=1.7-2 && \
    rm -rf /var/lib/apt/lists/*
