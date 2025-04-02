# Images for a multitude of purposes
Repository for docker, apptainer, etc. images

## Docker

### Rocky9

#### base-build

```docker pull ghcr.io/jose-d/images/rocky9_base-build:latest```

Basic build image based on Rocky Linux 9 containing common building dependencies like `crb`, `Development Tools`, etc.

#### pmix-build

```docker pull ghcr.io/jose-d/images/rocky9_pmix-build:latest```

Image extending `base-build` with pmi-x build dependencies.

#### slurm-build

Image extending `base-build` with pmi-x build dependencies, especially nvidia libs, munge, jwt, mariadb, etc..



