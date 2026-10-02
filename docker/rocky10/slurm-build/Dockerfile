ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images
ARG IMAGE_TAG=latest

FROM ${IMAGE_REPOSITORY}/rocky10_base_nv-build:${IMAGE_TAG}

# Same Slurm build dependencies as rocky9/slurm-build, except:
# - llhttp-devel supplies the HTTP parser for Slurm 26.05 slurmrestd;
#   older Slurm releases need a separately rebuilt http-parser package;
# - rdma-core-devel (libibmad/libibumad, for acct_gather_interconnect_ofed) and
#   UCX come from the DOCA repository configured in rocky10/base-build;
# - librdkafka-devel (jobcomp_kafka) and freeipmi-devel come from CRB;
# - libjwt-devel, libssh2-devel and gtk2-devel come from EPEL10;
# - python3-sphinx comes from CRB instead of an unpinned pip install.
RUN dnf install -y zlib-devel hwloc-devel libevent-devel python3-devel jansson-devel && \
    dnf install -y libjwt-devel pam-devel perl-ExtUtils-MakeMaker python3 readline-devel \
        mariadb-devel numactl-devel lua-devel json-c-devel libX11-devel libssh2-devel \
        libyaml-devel libcurl-devel lz4-devel freeipmi-devel dbus-devel librdkafka-devel \
        rdma-core-devel ucx ucx-devel llhttp-devel && \
# logrotate is a runtime dependency of the locally built munge RPM, which
# build_slurm.sh installs with every other repository disabled.
    dnf install -y createrepo_c gtk2-devel python3-sphinx logrotate && \
    dnf clean all && \
    rm -rf /var/cache/dnf
