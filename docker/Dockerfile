FROM ubuntu:20.04

COPY tzdata_install.sh /
RUN /tzdata_install.sh

COPY update_sources.sh /
RUN /update_sources.sh

RUN dpkg --add-architecture arm64
RUN apt-get update && apt-get install -y \
  bc \
  build-essential \
  crossbuild-essential-arm64 \
  sudo \
  pkg-config \
  curl \
  wget \
  git \
  vim \
  debhelper \
  automake \
  autoconf \
  libtool \
  libatasmart-dev \
  libatasmart-dev:arm64 \
  libjansson-dev \
  libjansson-dev:arm64 \
  libpcre3-dev \
  libpcre3-dev:arm64

ARG KUSER=kbuild
ARG KGROUP=kbuild
ARG KUID=1000
ARG KGID=1000

RUN groupadd --gid ${KGID} ${KGROUP}
RUN useradd -m -e '' -s /bin/bash --gid ${KGID} --uid ${KUID} ${KUSER}
RUN echo '${KUSER} ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
