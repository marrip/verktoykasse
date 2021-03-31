FROM python:3.7.10-slim-buster AS download
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.20.1-2+deb10u3 build-essential=12.6 cmake=3.13.4-1 zlib1g-dev=1:1.2.11.dfsg-1 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/SciLifeLab/TIDDIT.git
WORKDIR /TIDDIT
RUN ./INSTALL.sh
ENV PATH=$PATH:/TIDDIT
