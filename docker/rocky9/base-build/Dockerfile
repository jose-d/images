# Base build image of Rocky Linux 9

ARG IMAGE_REPOSITORY=ghcr.io/jose-d/images
ARG IMAGE_TAG=latest

FROM ${IMAGE_REPOSITORY}/rhel9_doca-base:${IMAGE_TAG}

RUN dnf -y update
# not sure if we really need crb, but if we do, we need dnf-plugins-core too:
RUN dnf install -y dnf-plugins-core
RUN dnf -y config-manager --set-enabled crb
RUN dnf -y groupinstall 'Development Tools'
RUN dnf -y install librdkafka-devel bash-completion rpmdevtools automake autoconf libtool make pkg-config less vim flex bison cmake which zlib-devel doxygen which wget

RUN dnf clean all
