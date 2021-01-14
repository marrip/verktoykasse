FROM ubuntu:18.04 AS download
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.17.1-1ubuntu0.7 ca-certificates=20201027ubuntu0.18.04.1 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/seandavi/SDST.git

FROM python:2.7.18-buster
WORKDIR /SDST
COPY --from=download /SDST/SDST ./SDST
COPY --from=download /SDST/scripts ./scripts
COPY --from=download /SDST/setup.py .
RUN python setup.py build
RUN python setup.py install
