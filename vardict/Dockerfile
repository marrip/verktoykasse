FROM ubuntu:20.04 AS download
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.25.1-1ubuntu3.1 ca-certificates=20210119~20.04.1 default-jre=2:1.11-72 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone -b $VERSION https://github.com/AstraZeneca-NGS/VarDict.git
RUN git clone -b $VERSION https://github.com/AstraZeneca-NGS/VarDictJava.git
WORKDIR /VarDictJava
RUN ./gradlew clean installDist

FROM ubuntu:20.04
ENV DEBIAN_FRONTEND=noninteractive \
    JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
RUN apt-get update && \
    apt-get install -y --no-install-recommends r-base=3.6.3-2 default-jre=2:1.11-72 libperl4-corelibs-perl=0.004-2 && \
    rm -rf /var/lib/apt/lists/*
COPY --from=download /VarDictJava/build/install/VarDict/bin /usr/local/bin
COPY --from=download /VarDictJava/build/install/VarDict/lib /usr/local/lib
COPY --from=download /VarDict/test*.R /usr/local/bin/
COPY --from=download /VarDict/var2vcf_*.pl /usr/local/bin/
