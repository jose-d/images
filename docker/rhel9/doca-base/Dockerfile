# DOCA base image based on Rocky Linux 9 (RHEL9-compatible)
# Installs doca-host from the NVIDIA/Mellanox DOCA repository

FROM rockylinux:9

ARG DOCA_VERSION=3.3.0
ARG EL_VERSION=rhel9
ARG DOCA_GPG_KEY_URL

RUN DOCA_REPO_NAME="doca-${DOCA_VERSION}" && \
    DOCA_REPO_URL="https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/" && \
    DOCA_REPO_GPG_URL="${DOCA_GPG_KEY_URL:-${DOCA_REPO_URL}GPG-KEY-Mellanox.pub}" && \
    rpm --import "${DOCA_REPO_GPG_URL}" && \
    printf '%s\n' \
        "[${DOCA_REPO_NAME}]" \
        "name=${DOCA_REPO_NAME}" \
        "enabled=1" \
        "baseurl=${DOCA_REPO_URL}" \
        "gpgcheck=1" \
        "cost=10" \
        "gpgkey=${DOCA_REPO_GPG_URL}" \
        > "/etc/yum.repos.d/${DOCA_REPO_NAME}.repo"
RUN dnf -y install --setopt=gpgcheck=1 doca-ofed
RUN dnf clean all
