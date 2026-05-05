ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images
ARG IMAGE_TAG=latest

FROM ${IMAGE_REPOSITORY}/rhel8_doca-base:${IMAGE_TAG}

RUN dnf update -y && \
    dnf install -y dnf-plugins-core && \
    dnf config-manager --set-enabled powertools && \
    dnf install -y librdkafka-devel bash-completion createrepo_c rpm-build automake autoconf libtool make pkg-config less vim flex bison doxygen cmake bash-doc which wget && \
    dnf clean all
