ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images

FROM ${IMAGE_REPOSITORY}/rocky8_pmix-build:latest

RUN dnf upgrade -y && \
    dnf install -y epel-release && \
    dnf install -y libjwt-devel zlib-devel munge-devel pam-devel perl-ExtUtils-MakeMaker python3 readline-devel mariadb-devel numactl-devel libevent-devel hwloc-devel lua-devel json-c-devel pam-devel libX11-devel libssh2-devel libyaml-devel libcurl-devel lz4-devel freeipmi-devel http-parser-devel dbus-devel ucx ucx-devel&& \
    dnf install -y gtk2-devel && \
    dnf clean all
