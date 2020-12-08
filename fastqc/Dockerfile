FROM ubuntu:20.04
ARG VERSION
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y --no-install-recommends fastqc=$VERSION && \
    rm -rf /var/lib/apt/lists/*
