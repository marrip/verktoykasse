FROM python:3.7-slim-buster
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git ca-certificates make g++ zlib1g-dev && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/ablab/quast.git
WORKDIR /quast
RUN ./setup.py install
