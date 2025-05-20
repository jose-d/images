FROM ghcr.io/jose-d/images/rocky8_base-build:latest

RUN dnf -y update && \
    dnf install -y zlib-devel hwloc-devel libevent-devel python3-devel jansson-devel && \
    dnf install -y munge-devel && \
    dnf clean all

RUN python3 -m pip install --no-cache-dir sphinx
