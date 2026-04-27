FROM rockylinux:8

ARG NVML_VERSION=13-2
ARG NV_DRIVER_VERSION=open-dkms

RUN dnf update -y && \
    dnf install -y dnf-plugins-core && \
    dnf config-manager --set-enabled powertools && \
    dnf install -y rpm-build automake autoconf libtool make pkg-config less vim flex bison doxygen cmake bash-doc which wget && \
    dnf clean all

# we go with precompiled nvidia-driver to save time..
RUN dnf config-manager --add-repo https://developer.download.nvidia.com/compute/cuda/repos/rhel8/x86_64/cuda-rhel8.repo && \
    dnf -y module install nvidia-driver:${NV_DRIVER_VERSION} && \
    dnf clean all && \
    dnf -y install --nobest cuda-nvml-devel-$NVML_VERSION cuda-$NVML_VERSION && \
    dnf clean all
