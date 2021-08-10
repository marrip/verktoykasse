FROM ubuntu:20.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends bedtools=2.27.1+dfsg-4ubuntu1 samtools=1.10-3 bcftools=1.10.2-2 bwa=0.7.17-4 tabix=1.10.2-3 && \
    rm -rf /var/lib/apt/lists/*
