ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images
ARG IMAGE_TAG=latest

FROM ${IMAGE_REPOSITORY}/rocky8_base_nv-build:${IMAGE_TAG}

RUN dnf -y update && \
    dnf install -y zlib-devel hwloc-devel libevent-devel python3-devel jansson-devel && \
    dnf clean all

RUN python3 -m pip install --no-cache-dir sphinx
