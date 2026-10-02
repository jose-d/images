# Images for a multitude of purposes
Repository for docker, apptainer, etc. images

## Docker

### RHEL8 (Rocky Linux 8)

#### doca-base

```docker pull ghcr.io/jose-d/images/rhel8_doca-base:latest```

Base image based on Rocky Linux 8 (RHEL8-compatible) with `doca-host` installed from the [NVIDIA/Mellanox DOCA 3.3.0 RHEL8 repository](https://linux.mellanox.com/public/repo/doca/3.3.0/rhel8/x86_64/).

### RHEL9 (Rocky Linux 9)

#### doca-base

```docker pull ghcr.io/jose-d/images/rhel9_doca-base:latest```

Base image based on Rocky Linux 9 (RHEL9-compatible) with `doca-host` installed from the [NVIDIA/Mellanox DOCA 3.3.0 RHEL9 repository](https://linux.mellanox.com/public/repo/doca/3.3.0/rhel9/x86_64/).

### Rocky8

#### base-build

```docker pull ghcr.io/jose-d/images/rocky8_base-build:latest```

Basic build image based on Rocky Linux 8 containing common building dependencies like `powertools`, `rpm-build`, etc.

#### base_nv-build

```docker pull ghcr.io/jose-d/images/rocky8_base_nv-build:latest```

Image extending `base-build` with the NVIDIA NVML development and runtime libraries needed for Slurm integration.

#### pmix-build

```docker pull ghcr.io/jose-d/images/rocky8_pmix-build:latest```

Image extending `base_nv-build` with pmix build dependencies.

#### slurm-build

```docker pull ghcr.io/jose-d/images/rocky8_slurm-build:latest```

Image extending `pmix-build` with Slurm build dependencies like munge, jwt, mariadb, etc.

### Rocky9

#### base-build

```docker pull ghcr.io/jose-d/images/rocky9_base-build:latest```

Basic build image based on Rocky Linux 9 containing common building dependencies like `crb`, `Development Tools`, etc.

#### base_nv-build

```docker pull ghcr.io/jose-d/images/rocky9_base_nv-build:latest```

Image extending `base-build` with the NVIDIA NVML development and runtime libraries needed for Slurm integration.

#### pmix-build

```docker pull ghcr.io/jose-d/images/rocky9_pmix-build:latest```

Image extending `base_nv-build` with pmix build dependencies.

#### slurm-build

```docker pull ghcr.io/jose-d/images/rocky9_slurm-build:latest```

Image extending `pmix-build` with Slurm build dependencies like munge, jwt, mariadb, etc.

### Rocky10

Built by the `Build Rocky10 Docker imgs` workflow (`docker_rocky10_build_base.yml`).
There is no separate `rhel10_doca-base` layer: `rocky10_base-build` starts from the
digest-pinned upstream `quay.io/rockylinux/rockylinux:10` image and takes only the
DOCA userspace build dependencies (`rdma-core-devel`, `ucx`, `ucx-devel`) from the
[NVIDIA DOCA 3.5.0 RHEL10 repository](https://linux.mellanox.com/public/repo/doca/3.5.0/rhel10/x86_64/),
the DOCA release installed on the EL10 GPU nodes. CRB and EPEL 10 are enabled.

#### base-build

```docker pull ghcr.io/jose-d/images/rocky10_base-build:latest```

Basic build image based on Rocky Linux 10 with `crb`, EPEL 10, `Development Tools`, `rpm-build` and the DOCA userspace development packages.

#### base_nv-build

```docker pull ghcr.io/jose-d/images/rocky10_base_nv-build:latest```

Image extending `base-build` with `cuda-nvml-devel` (CUDA 13.4 series by default) from NVIDIA's RHEL10 CUDA repository. The driver's `libnvidia-ml` is not installed; Slurm links against the stub library.

#### pmix-build

```docker pull ghcr.io/jose-d/images/rocky10_pmix-build:latest```

Image extending `base_nv-build` with PMIx build dependencies.

#### slurm-build

```docker pull ghcr.io/jose-d/images/rocky10_slurm-build:latest```

Image extending `base_nv-build` with Slurm build dependencies. `http-parser-devel` is not available for EL10 (BaseOS, AppStream, CRB or EPEL 10), so Slurm builds from this image cannot include `slurmrestd`.

The images can also be built locally, for example with podman:

```bash
podman build -t localhost/jose-d/images/rocky10_base-build:local docker/rocky10/base-build
for image in base_nv-build pmix-build slurm-build; do
    podman build --build-arg IMAGE_REPOSITORY=localhost/jose-d/images --build-arg IMAGE_TAG=local \
        -t "localhost/jose-d/images/rocky10_${image}:local" "docker/rocky10/${image}"
done
```
