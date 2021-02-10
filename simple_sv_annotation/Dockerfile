FROM ubuntu:18.04 AS download
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.17.1-1ubuntu0.7 ca-certificates=20210119~18.04.1 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/AstraZeneca-NGS/simple_sv_annotation.git

FROM python:2.7.18-buster
RUN pip install PyVcf==0.6.8
WORKDIR /simple_sv_annotation
COPY --from=download /simple_sv_annotation/simple_sv_annotation.py .
ENV PATH=$PATH:/simple_sv_annotation
