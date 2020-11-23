FROM python:2.7.18-buster
ARG CONIFER_VERSION
RUN echo $CONIFER_VERSION
RUN apt-get update && \
    apt-get install -y git
RUN git clone -b "$CONIFER_VERSION" --depth 1 "https://github.com/nkrumm/CoNIFER.git"
RUN pip install tables
WORKDIR /CoNIFER
