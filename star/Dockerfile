FROM ubuntu:20.04 AS compiler
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.25.1-1ubuntu3.2 ca-certificates=20210119~20.04.2 build-essential=12.8ubuntu1.1 zlib1g-dev=1:1.2.11.dfsg-2ubuntu1.2 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/alexdobin/STAR.git
WORKDIR /STAR/source
RUN make

FROM ubuntu:20.04
RUN apt-get update && \
    apt-get install -y --no-install-recommends libgomp1=10.3.0-1ubuntu1~20.04 && \
    rm -rf /var/lib/apt/lists/*
COPY --from=compiler /STAR/source/STAR /usr/local/bin/
