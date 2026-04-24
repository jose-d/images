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

### Rocky9

#### base-build

```docker pull ghcr.io/jose-d/images/rocky9_base-build:latest```

Basic build image based on Rocky Linux 9 containing common building dependencies like `crb`, `Development Tools`, etc.

#### pmix-build

```docker pull ghcr.io/jose-d/images/rocky9_pmix-build:latest```

Image extending `base-build` with pmi-x build dependencies.

#### slurm-build

```docker pull ghcr.io/jose-d/images/rocky9_slurm-build:latest```

Image extending `base-build` with pmi-x build dependencies, especially nvidia libs, munge, jwt, mariadb, etc..

