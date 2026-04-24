# DOCA base image based on Rocky Linux 8 (RHEL8-compatible)
# Installs doca-host from the NVIDIA/Mellanox DOCA repository

FROM rockylinux:8

ARG DOCA_VERSION=3.3.0
ARG EL_VERSION=rhel8
ARG DOCA_GPG_KEY_URL

RUN if [ -n "${DOCA_GPG_KEY_URL}" ]; then \
        rpm --import "${DOCA_GPG_KEY_URL}"; \
    else \
        rpm --import "https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/GPG-KEY-Mellanox.pub"; \
    fi
RUN DOCA_REPO_NAME="doca-${DOCA_VERSION}" && \
    DOCA_REPO_URL="https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/" && \
    DOCA_REPO_GPG_URL="${DOCA_GPG_KEY_URL:-${DOCA_REPO_URL}GPG-KEY-Mellanox.pub}" && \
    cat <<EOF > "/etc/yum.repos.d/${DOCA_REPO_NAME}.repo"
[${DOCA_REPO_NAME}]
name=${DOCA_REPO_NAME}
enabled=1
baseurl=${DOCA_REPO_URL}
gpgcheck=1
cost=10
gpgkey=${DOCA_REPO_GPG_URL}
EOF
RUN dnf repolist -v
RUN dnf -y install --setopt=gpgcheck=1 doca-ofed
RUN dnf clean all
