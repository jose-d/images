# DOCA base image based on Rocky Linux 8 (RHEL8-compatible)
# Installs doca-host from the NVIDIA/Mellanox DOCA repository

FROM rockylinux:8

ARG DOCA_VERSION=3.3.0
ARG EL_VERSION=el8

RUN dnf install -y dnf-plugins-core && \
    rpm --import https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/RPM-GPG-KEY-Mellanox && \
    dnf config-manager --add-repo https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/ && \
    dnf -y install --setopt=gpgcheck=1 doca-host && \
    dnf clean all
