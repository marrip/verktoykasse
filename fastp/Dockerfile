FROM ubuntu:20.04
ARG FASTP_VERSION
RUN apt-get update && \
    apt-get install -y wget && \
    rm -rf /var/lib/apt/lists/*
RUN wget -O /usr/local/bin/fastp http://opengene.org/fastp/fastp && \
    chmod a+x /usr/local/bin/fastp
