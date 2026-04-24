# DOCA base image based on Rocky Linux 8 (RHEL8-compatible)
# Installs doca-host from the NVIDIA/Mellanox DOCA 3.3.0 RHEL8 repository

FROM rockylinux:8

RUN dnf install -y dnf-plugins-core && \
    rpm --import https://linux.mellanox.com/public/repo/doca/3.3.0/rhel8/x86_64/RPM-GPG-KEY-Mellanox && \
    dnf config-manager --add-repo https://linux.mellanox.com/public/repo/doca/3.3.0/rhel8/x86_64/ && \
    dnf -y install --setopt=gpgcheck=1 doca-host && \
    dnf clean all
