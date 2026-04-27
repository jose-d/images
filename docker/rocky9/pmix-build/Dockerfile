ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images

FROM ${IMAGE_REPOSITORY}/rocky9_base_nv-build:latest

RUN dnf install -y zlib-devel hwloc-devel libevent-devel python3-devel jansson-devel
RUN dnf clean all
RUN python3 -m pip install --no-cache-dir sphinx
