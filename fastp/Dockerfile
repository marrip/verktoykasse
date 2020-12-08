FROM ubuntu:20.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.19.4-1ubuntu2.2 ca-certificates=20201027ubuntu0.18.04.1 && \
    rm -rf /var/lib/apt/lists/*
RUN wget -O /usr/local/bin/fastp http://opengene.org/fastp/fastp && \
    chmod a+x /usr/local/bin/fastp
