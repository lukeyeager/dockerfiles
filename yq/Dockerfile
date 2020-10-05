FROM ubuntu:20.04
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        jq \
        python3-pip \
    && rm -rf /var/lib/apt/lists/*
RUN pip3 install --no-cache-dir \
        yq==2.11.1
