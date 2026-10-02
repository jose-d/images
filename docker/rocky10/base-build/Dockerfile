# Base build image of Rocky Linux 10
#
# Unlike rocky8/rocky9 there is no separate rhel10_doca-base layer: the base is
# the upstream Rocky Linux 10 image, pinned by digest, and only the DOCA
# userspace build dependencies (rdma-core-devel, UCX) are taken from the
# versioned NVIDIA DOCA repository, matching the DOCA release on the EL10 GPU
# nodes. Kernel/kmod parts of doca-ofed are not needed to build Slurm.

ARG BASE_IMAGE=quay.io/rockylinux/rockylinux:10@sha256:827d37bc128288ccf160ee318bb3cb92d591164cb217e92f8bc61e3982ae1834

FROM ${BASE_IMAGE}

ARG DOCA_VERSION=3.5.0
ARG EL_VERSION=rhel10

RUN DOCA_REPO_NAME="doca-${DOCA_VERSION}" && \
    DOCA_REPO_URL="https://linux.mellanox.com/public/repo/doca/${DOCA_VERSION}/${EL_VERSION}/x86_64/" && \
    printf '%s\n' \
        "[${DOCA_REPO_NAME}]" \
        "name=${DOCA_REPO_NAME}" \
        "enabled=1" \
        "baseurl=${DOCA_REPO_URL}" \
        "gpgcheck=1" \
        "cost=10" \
        "gpgkey=${DOCA_REPO_URL}RPM-GPG-KEY-doca" \
        > "/etc/yum.repos.d/${DOCA_REPO_NAME}.repo" && \
    cat "/etc/yum.repos.d/${DOCA_REPO_NAME}.repo"

RUN dnf -y update && \
    dnf -y install dnf-plugins-core epel-release && \
    dnf -y config-manager --set-enabled crb && \
    dnf -y groupinstall 'Development Tools' && \
    dnf -y install rpm-build rpmdevtools redhat-rpm-config createrepo_c \
        librdkafka-devel bash-completion automake autoconf libtool make \
        pkgconf-pkg-config less vim-minimal flex bison cmake which zlib-devel \
        doxygen wget findutils && \
    dnf -y install rdma-core-devel ucx ucx-devel && \
    dnf clean all && \
    rm -rf /var/cache/dnf
