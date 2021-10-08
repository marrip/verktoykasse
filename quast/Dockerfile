FROM python:3.7-slim-buster
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.20.1-2+deb10u3 ca-certificates=20200601~deb10u2 make=4.2.1-1.2 g++=4:8.3.0-1 zlib1g-dev=1:1.2.11.dfsg-1 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/ablab/quast.git
WORKDIR /quast
RUN ./setup.py install
