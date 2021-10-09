FROM python:3.7-slim-buster
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.20.1-2+deb10u3 wget=1.20.1-1.1 ca-certificates=20200601~deb10u2 make=4.2.1-1.2 cmake=3.13.4-1 gcc=4:8.3.0-1 g++=4:8.3.0-1 zlib1g-dev=1:1.2.11.dfsg-1 default-jre=2:1.11-71 samtools=1.9-4 ncbi-blast+=2.8.1-1+deb10u1 bowtie2=2.3.4.3-1 && \
    rm -rf /var/lib/apt/lists/*
RUN wget https://github.com/ablab/spades/releases/download/v3.15.3/SPAdes-3.15.3-Linux.tar.gz && \
    tar -xzf SPAdes-3.15.3-Linux.tar.gz && \
    rm SPAdes-3.15.3-Linux.tar.gz
ENV PATH=$PATH:/SPAdes-3.15.3-Linux/bin
RUN git clone --recursive -b 1.4.3 https://github.com/isovic/racon.git /racon
WORKDIR /racon/build
RUN cmake -DCMAKE_BUILD_TYPE=Release .. && \
    make && \
    mv /racon/build/bin/racon /usr/local/bin/ && \
    rm -rf /racon
WORKDIR /
RUN wget https://github.com/broadinstitute/pilon/releases/download/v1.23/pilon-1.23.jar
RUN mv /pilon-*.jar /usr/local/bin/
RUN git clone -b $VERSION https://github.com/rrwick/Unicycler.git /unicycler
WORKDIR /unicycler
RUN python3 setup.py install
