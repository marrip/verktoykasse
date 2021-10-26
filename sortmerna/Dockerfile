FROM ubuntu:20.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.20.3-1ubuntu1 ca-certificates=20210119~20.04.2 && \
    rm -rf /var/lib/apt/lists/*
RUN wget https://github.com/biocore/sortmerna/releases/download/v$VERSION/sortmerna-$VERSION-Linux.tar.gz && \
    tar -xzvf /sortmerna-$VERSION-Linux.tar.gz && \
    rm /sortmerna-$VERSION-Linux.tar.gz
ENV PATH=$PATH:/sortmerna-$VERSION-Linux/bin
