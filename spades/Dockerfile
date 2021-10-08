FROM python:3.7-slim-buster
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.20.1-1.1 ca-certificates=20200601~deb10u2 && \
    rm -rf /var/lib/apt/lists/*
RUN wget https://github.com/ablab/spades/releases/download/v$VERSION/SPAdes-$VERSION-Linux.tar.gz && \
    tar -xzf SPAdes-$VERSION-Linux.tar.gz && \
    rm SPAdes-$VERSION-Linux.tar.gz
ENV PATH=$PATH:/SPAdes-$VERSION-Linux/bin
