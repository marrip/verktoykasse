FROM ubuntu:20.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.20.3-1ubuntu2 && \
    rm -rf /var/lib/apt/lists/*
ENV ILLUMINA_REPO=https://github.com/Illumina/interop/releases/download \
    FILE="InterOp-$VERSION-Linux-GNU.tar.gz" \
    PATH="/InterOp-$VERSION-Linux-GNU/bin:$PATH"
RUN wget --no-check-certificate -q $ILLUMINA_REPO/v$VERSION/$FILE && \
    tar -xvf $FILE && \
    rm $FILE
