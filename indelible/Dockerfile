FROM python:3.7.10-slim-buster AS download
ARG VERSION
RUN apt-get update && \
    apt-get install -y --no-install-recommends git=1:2.20.1-2+deb10u3 && \
    rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/eugenegardner/indelible.git
WORKDIR /indelible
RUN git checkout "$VERSION"
#RUN python3 -m venv venv/ && \
#    /bin/bash -c "source venv/bin/activate"

FROM python:3.7.10-slim-buster
RUN apt-get update && \
    apt-get install -y --no-install-recommends build-essential=12.6 zlib1g-dev=1:1.2.11.dfsg-1 bedtools=2.27.1+dfsg-4 && \
    rm -rf /var/lib/apt/lists/*
COPY --from=download /indelible/indelible.py /indelible/indelible.py
COPY --from=download /indelible/indelible/* /indelible/indelible/
COPY --from=download /indelible/vr_runner_scripts/* /indelible/vr_runner_scripts/
RUN pip install cython==0.29.22 numpy==1.17.2 pandas==0.25.1 pybedtools==0.8.0 pyfaidx==0.5.5.2 pysam==0.16.0.1 scipy==1.3.1 scikit-learn==0.21.3 PyYAML==5.1.2 Biopython==1.74 intervaltree==3.0.2
ENV PATH=$PATH:/indelible
