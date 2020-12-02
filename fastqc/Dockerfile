FROM ubuntu:20.04
ARG FASTQC_VERSION
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y fastqc=$FASTQC_VERSION && \
    rm -rf /var/lib/apt/lists/*
