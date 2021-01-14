FROM ubuntu:18.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.19.4-1ubuntu2.2 ca-certificates=20201027ubuntu0.18.04.1 unzip=6.0-21ubuntu1.1 default-jre=2:1.11-68ubuntu1~18.04.1 && \
    rm -rf /var/lib/apt/lists/*
RUN wget "https://snpeff.blob.core.windows.net/versions/snpEff_v${VERSION}_core.zip" && \
    unzip snpEff_v${VERSION}_core.zip && \
    rm -rf snpEff_v${VERSION}_core.zip /snpEff/examples/
RUN echo "test.genome : Homo sapiens AADACL3" >> /snpEff/snpEff.config
