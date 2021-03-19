FROM ubuntu:18.04 AS download
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.17.1-1ubuntu0.8 ca-certificates=20210119~18.04.1 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/seandavi/SDST.git

FROM python:2.7.18-buster
RUN pip install numpy==1.16.6
WORKDIR /SDST
COPY --from=download /SDST/SDST ./SDST
COPY --from=download /SDST/scripts ./scripts
COPY --from=download /SDST/setup.py .
RUN python setup.py build
RUN python setup.py install
