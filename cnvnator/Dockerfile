FROM ubuntu:20.04 AS download
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.20.3-1ubuntu1 ca-certificates=20210119~20.04.1 build-essential=12.8ubuntu1.1 zlib1g-dev=1:1.2.11.dfsg-2ubuntu1.2 libncurses5-dev=6.2-0ubuntu2 libncursesw5-dev=6.2-0ubuntu2 libbz2-dev=1.0.8-2 liblzma-dev=5.2.4-1ubuntu1 autoconf=2.69-11.1 libcurl4-openssl-dev=7.68.0-1ubuntu2.5 unzip=6.0-25ubuntu1 libreadline-dev=8.0-4 libfreetype6-dev=2.10.1-2ubuntu0.1 && \
    rm -rf /var/lib/apt/lists/*
RUN wget "https://root.cern/download/root_v6.22.06.Linux-ubuntu20-x86_64-gcc9.3.tar.gz" && \
    tar -xzvf root_v6.22.06.Linux-ubuntu20-x86_64-gcc9.3.tar.gz && \
    rm root_v6.22.06.Linux-ubuntu20-x86_64-gcc9.3.tar.gz
RUN echo '/root/lib' > /etc/ld.so.conf.d/root.conf && \
    ldconfig
ENV ROOTSYS=/root
RUN wget "https://github.com/abyzovlab/CNVnator/releases/download/v0.4.1/CNVnator_${VERSION}.zip" && \
    unzip CNVnator_$VERSION.zip && \
    mv /CNVnator_$VERSION /CNVnator && \
    rm CNVnator_$VERSION.zip
WORKDIR /CNVnator/src
RUN wget "https://github.com/samtools/samtools/releases/download/1.12/samtools-1.12.tar.bz2" && \
    tar -xvf samtools-1.12.tar.bz2 && \
    mv samtools-1.12 samtools && \
    rm samtools-1.12.tar.bz2
WORKDIR /CNVnator/src/samtools
RUN make
WORKDIR /CNVnator/src
RUN sed -i '1s/^/#include <set>\n/' IO.cpp && \
    make

FROM ubuntu:20.04
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y --no-install-recommends python3=3.8.2-0ubuntu2 python3-matplotlib=3.1.2-1ubuntu4 python3-scipy=1.3.3-3build1 python3-tk=3.8.10-0ubuntu1~20.04 libcurl4-openssl-dev=7.68.0-1ubuntu2.5 libgomp1=10.3.0-1ubuntu1~20.04 build-essential=12.8ubuntu1.1 && \
    rm -rf /var/lib/apt/lists/*
COPY --from=download /root/lib /opt/root/lib
COPY --from=download /root/etc /opt/root/etc
COPY --from=download /root/include /opt/root/include
RUN echo '/opt/root/lib' > /etc/ld.so.conf.d/root.conf && \
    ldconfig
ENV ROOTSYS=/opt/root
COPY --from=download /CNVnator/src/cnvnator /usr/local/bin/
COPY --from=download /CNVnator/src/*.py /usr/local/bin/
COPY --from=download /CNVnator/src/cnvnator2VCF.pl /usr/local/bin/
RUN ln -s /usr/bin/python3 /usr/bin/python
