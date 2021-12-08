FROM ubuntu:18.04 AS download
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget=1.19.4-1ubuntu2.2 ca-certificates=20210119~18.04.2 unzip=6.0-21ubuntu1.1 && \
    rm -rf /var/lib/apt/lists/*
RUN wget "http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-${VERSION}.zip" && \
    unzip Trimmomatic-$VERSION.zip
 
FROM ubuntu:18.04
ARG VERSION
COPY --from=download /Trimmomatic-$VERSION/trimmomatic-$VERSION.jar /opt/
RUN apt-get update && \
    apt-get install -y --no-install-recommends default-jre=2:1.11-68ubuntu1~18.04.1 && \
    rm -rf /var/lib/apt/lists/*
