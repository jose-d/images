ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images
ARG IMAGE_TAG=latest

FROM ${IMAGE_REPOSITORY}/rocky10_base_nv-build:${IMAGE_TAG}

# python3-sphinx comes from CRB instead of an unpinned pip install.
# perl-interpreter: used by rpm's perl dependency generators for PMIx.
RUN dnf install -y zlib-devel hwloc-devel libevent-devel python3-devel jansson-devel ucx ucx-devel python3-sphinx perl-interpreter && \
    dnf clean all && \
    rm -rf /var/cache/dnf
