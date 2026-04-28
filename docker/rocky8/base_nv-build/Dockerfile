ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images

FROM ${IMAGE_REPOSITORY}/rocky8_base-build:latest

ARG NVML_VERSION=13-2
ARG NVIDIA_REPO=https://developer.download.nvidia.com/compute/cuda/repos/rhel8/x86_64/cuda-rhel8.repo

# install the CUDA NVML development and runtime libraries needed for Slurm integration
RUN dnf config-manager --add-repo ${NVIDIA_REPO} && \
    dnf -y install --nobest libnvidia-ml cuda-nvml-devel-$NVML_VERSION && \
    dnf clean all && \
    rm -rf /var/cache/dnf
