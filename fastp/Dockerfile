FROM ubuntu:20.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.20.3-1ubuntu1 ca-certificates=20201027ubuntu0.20.04.1 && \
    rm -rf /var/lib/apt/lists/*
RUN wget -O /usr/local/bin/fastp http://opengene.org/fastp/fastp && \
    chmod a+x /usr/local/bin/fastp
