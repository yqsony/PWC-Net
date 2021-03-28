# syntax = docker/dockerfile:1.0-experimental

FROM nvidia/cudagl:8.0-devel-ubuntu18.04


RUN \
  apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install --fix-missing --no-install-recommends -y \
  apt-transport-https \
  ca-certificates \
  ccache \
  curl \
  freeglut3-dev \
  gdb \
  gdbserver \
  gfortran \
  git \
  openssh-client \
  python2.7 \
  python2-pip \
  python2-setuptools \
  python2-tk \
  qt5-qmake \
  qtbase5-dev \
  software-properties-common \
  sudo \
  vlc \
  unzip \
  && add-apt-repository ppa:deadsnakes/ppa \
  && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - \
  && apt-key fingerprint 0EBFCD88 \
  && add-apt-repository \
     'deb [arch=amd64] https://download.docker.com/linux/ubuntu \
     bionic stable' \
  && apt-get update \
  && apt-get install -y docker-ce-cli python2.7 \
  && curl -fsSL https://apt.kitware.com/keys/kitware-archive-latest.asc | gpg --dearmor - \
     > /etc/apt/trusted.gpg.d/kitware.gpg \
  && add-apt-repository \
     'deb https://apt.kitware.com/ubuntu/ \
     bionic main' \
  && apt-get update \
  && apt-get install -y cmake \
  && rm -rf /var/lib/apt/lists/*

RUN pip install \
  cython \
  numpy \
  wheel
# Most packages should be specified here.
RUN pip2 install \
  http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp27-cp27mu-manylinux1_x86_64.whl \
  torchvision==0.3.0 \
  visdom \
  dominate \
  opencv-python==3.4.2.18 \
  cffi==0.8.0 \
  pandas \
  pillow \