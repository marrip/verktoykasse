FROM python:3.6.11-slim-buster
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends r-base=3.5.2-1 build-essential=12.6 gfortran=4:8.3.0-1 && \
    rm -rf /var/lib/apt/lists/*
RUN pip install pomegranate==0.10 cnvkit==$VERSION
RUN Rscript -e 'install.packages("BiocManager")'
RUN Rscript -e 'BiocManager::install("DNAcopy")'
