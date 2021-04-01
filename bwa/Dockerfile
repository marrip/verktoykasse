FROM broadinstitute/gatk:4.1.9.0
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends bwa=${VERSION}-1ubuntu0.1 && \
    rm -rf /var/lib/apt/lists/*
