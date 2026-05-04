ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images
ARG IMAGE_TAG=latest

FROM ${IMAGE_REPOSITORY}/rocky9_base_nv-build:${IMAGE_TAG}

RUN dnf install -y zlib-devel hwloc-devel libevent-devel python3-devel jansson-devel && \
    dnf install -y epel-release && \
    dnf install -y libjwt-devel munge-devel pam-devel perl-ExtUtils-MakeMaker python3 readline-devel mariadb-devel numactl-devel lua-devel json-c-devel libX11-devel libssh2-devel libyaml-devel libcurl-devel lz4-devel freeipmi-devel http-parser-devel dbus-devel && \
    dnf install -y createrepo_c gtk2-devel && \
    dnf clean all

RUN python3 -m pip install --no-cache-dir sphinx
