# Base build image of Rocky Linux 9

FROM rockylinux:9

ARG NVML_VERSION=13-2
ARG NV_DRIVER_VERSION=580

RUN dnf -y update
# not sure if we really need crb, but if we do, we need dnf-plugins-core too:
RUN dnf install -y dnf-plugins-core
RUN dnf -y config-manager --set-enabled crb
RUN dnf -y groupinstall 'Development Tools'
RUN dnf -y install rpmdevtools automake autoconf libtool make pkg-config less vim flex bison cmake which zlib-devel doxygen which wget

RUN dnf clean all

# we go with precompiled nvidia-driver to save time..
RUN dnf config-manager --add-repo https://developer.download.nvidia.com/compute/cuda/repos/rhel9/x86_64/cuda-rhel9.repo && \
    dnf -y module install nvidia-driver:${NV_DRIVER_VERSION} && \
    dnf clean all && \
    dnf -y install --nobest cuda-nvml-devel-$NVML_VERSION cuda-$NVML_VERSION && \
    dnf clean all
