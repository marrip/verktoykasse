FROM python:3.7.10-slim-buster
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.20.1-2+deb10u3 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/J35P312/SVDB.git
WORKDIR /SVDB
RUN pip install -e .
