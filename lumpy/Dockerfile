FROM python:2.7.18-buster AS compiler
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.20.1-2+deb10u3 wget=1.20.1-1.1 ca-certificates=20200601~deb10u1 cmake=3.13.4-1 && \
    rm -rf /var/lib/apt/lists/*
RUN wget https://github.com/biod/sambamba/releases/download/v0.7.0/sambamba-0.7.0-linux-static.gz && \
    gunzip sambamba-0.7.0-linux-static.gz && \
    chmod a+x sambamba-0.7.0-linux-static
RUN git clone -b "$VERSION" --recursive --depth 1 "https://github.com/arq5x/lumpy-sv.git"
WORKDIR /lumpy-sv
RUN make

FROM python:2.7.18-buster
RUN apt-get update && \
    apt-get install -y --no-install-recommends samtools=1.9-4 gawk=1:4.2.1+dfsg-1 samblaster=0.1.24-2 && \
    rm -rf /var/lib/apt/lists/*
RUN pip install pysam==0.16.0.1 numpy==1.16.6
COPY --from=compiler /sambamba-0.7.0-linux-static /usr/local/bin/sambamba
COPY --from=compiler /lumpy-sv/bin/* /usr/local/bin/
COPY --from=compiler /lumpy-sv/scripts /home/scripts
RUN printf "LUMPY_HOME=/usr/local/bin/\\nLUMPY=/usr/local/bin/lumpy\\nSAMBLASTER=/usr/bin/samblaster\\nSAMBAMBA=/usr/local/bin/sambamba\\nSAMTOOLS=/usr/local/bin/samtools\\nPYTHON=/usr/local/bin/python\\nPAIREND_DISTRO=/home/scripts/pairend_distro.py\\nBAMGROUPREADS=/home/scripts/bamkit/bamgroupreads.py\\nBAMFILTERRG=/home/scripts/bamkit/bamfilterrg.py\\nBAMLIBS=/home/scripts/bamkit/bamlibs.py" > /usr/local/bin/lumpyexpress.config
