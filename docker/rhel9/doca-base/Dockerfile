# DOCA base image based on Rocky Linux 9 (RHEL9-compatible)
# Installs doca-host from the NVIDIA/Mellanox DOCA repository

FROM rockylinux:9

ARG DOCA_VERSION=3.3.0
ARG EL_VERSION=rhel9
ARG DOCA_GPG_KEY_URL

RUN dnf install -y dnf-plugins-core
RUN rpm --import ${DOCA_GPG_KEY_URL:-https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/GPG-KEY-Mellanox.pub}
RUN dnf config-manager --add-repo https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/
RUN dnf -y install --setopt=gpgcheck=1 doca-ofed
RUN dnf clean all
