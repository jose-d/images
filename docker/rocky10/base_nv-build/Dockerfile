ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images
ARG IMAGE_TAG=latest

FROM ${IMAGE_REPOSITORY}/rocky10_base-build:${IMAGE_TAG}

# The EL10 GPU nodes run CUDA 13.x with the nvidia-open driver. NVML headers and
# the libnvidia-ml.so stub come from cuda-nvml-devel; the driver's libnvidia-ml
# is deliberately not installed (Slurm strips the libnvidia-ml dependency and
# links against the stub). NVIDIA's rhel10 repository starts at 13-1.
ARG NVML_VERSION=13-4
ARG NVML_PACKAGE_VERSION=13.4.92-1
ARG NVIDIA_REPO=https://developer.download.nvidia.com/compute/cuda/repos/rhel10/x86_64/cuda-rhel10.repo

# Only NVML is taken from the CUDA repository. Without includepkgs, later
# libOpenCL.so.1 dependencies resolve to cuda-opencl-13-0 instead of the
# distribution's ocl-icd and drag in a second /usr/local/cuda-13.0 tree.
RUN dnf config-manager --add-repo ${NVIDIA_REPO} && \
    dnf config-manager --save \
        --setopt='cuda-rhel10-x86_64.includepkgs=cuda-nvml-devel-*,cuda-toolkit-*config-common*' && \
    dnf -y install "cuda-nvml-devel-${NVML_VERSION}${NVML_PACKAGE_VERSION:+-${NVML_PACKAGE_VERSION}}" && \
    dnf clean all && \
    rm -rf /var/cache/dnf
