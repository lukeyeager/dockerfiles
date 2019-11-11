FROM ubuntu:19.10
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        tshark \
    && rm -rf /var/lib/apt/lists/*
