FROM python:2.7.18-buster
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.20.1-2+deb10u3 ca-certificates=20200601~deb10u2 && \
    rm -rf /var/lib/apt/lists/*
RUN pip install tables==3.5.2
RUN git clone -b "$VERSION" --depth 1 "https://github.com/nkrumm/CoNIFER.git"
WORKDIR /CoNIFER
