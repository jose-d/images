FROM  ghcr.io/jose-d/images/rocky9_base-build:latest

RUN dnf install -y zlib-devel hwloc-devel libevent-devel python3-devel jansson-devel
RUN dnf clean all
RUN python3 -m pip install --no-cache-dir sphinx
