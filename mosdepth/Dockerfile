FROM ubuntu:18.04
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.19.4-1ubuntu2.2 ca-certificates=20201027ubuntu0.18.04.1 && \
    rm -rf /var/lib/apt/lists/*
WORKDIR /usr/local/bin
RUN wget "https://github.com/brentp/mosdepth/releases/download/${VERSION}/mosdepth"
RUN chmod a+x mosdepth

