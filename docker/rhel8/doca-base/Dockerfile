# DOCA base image based on Rocky Linux 8 (RHEL8-compatible)
# Installs doca-host from the NVIDIA/Mellanox DOCA repository

FROM rockylinux:8

ARG DOCA_VERSION=3.3.0
ARG EL_VERSION=rhel8

RUN DOCA_REPO_NAME="doca-${DOCA_VERSION}" && \
    DOCA_REPO_URL="https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/" && \
    DOCA_REPO_GPG_URL="https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/GPG-KEY-Mellanox.pub" && \
    printf '%s\n' \
        "[${DOCA_REPO_NAME}]" \
        "name=${DOCA_REPO_NAME}" \
        "enabled=1" \
        "baseurl=${DOCA_REPO_URL}" \
        "gpgcheck=1" \
        "cost=10" \
        "gpgkey=${DOCA_REPO_GPG_URL}" \
        > "/etc/yum.repos.d/${DOCA_REPO_NAME}.repo" && \
    cat "/etc/yum.repos.d/${DOCA_REPO_NAME}.repo"
RUN dnf repolist -v
RUN dnf clean all
RUN dnf -y install doca-ofed
RUN dnf clean all
