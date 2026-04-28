ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images

FROM ${IMAGE_REPOSITORY}/rocky9_base-build:latest

ARG NVML_VERSION=13-2

# install the CUDA NVML development and runtime libraries needed for Slurm integration
RUN dnf config-manager --add-repo https://developer.download.nvidia.com/compute/cuda/repos/rhel9/x86_64/cuda-rhel9.repo && \
    dnf -y install --nobest cuda-nvml-$NVML_VERSION cuda-nvml-devel-$NVML_VERSION && \
    dnf clean all && \
    rm -rf /var/cache/dnf
