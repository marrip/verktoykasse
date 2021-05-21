FROM ubuntu:20.04
ARG VERSION
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.25.1-1ubuntu3.1 ca-certificates=20210119~20.04.1 samtools=1.10-3 r-base=3.6.3-2 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/AstraZeneca-NGS/VarDict.git
ENV PATH=$PATH:/VarDict
