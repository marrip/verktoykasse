FROM python:2.7.18-buster
RUN apt-get update && \
    apt-get install -y git
RUN git clone -b 0.2.2 --depth 1 https://github.com/nkrumm/CoNIFER.git
RUN pip install tables
WORKDIR /CoNIFER
