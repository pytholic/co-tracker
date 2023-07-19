FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu22.04

# Metadata
LABEL maintainer="rajahaseeb147@gmail.com" \
    project-name="Co-Tracker" \
    com.droid-slam.version="0.0.1" \
    com.droid-slam.realease-data="2023.07.19"

# Set arguments and env variables
ARG DEBIAN_FRONTEND=noninteractive
ENV NVIDIA_VISIBLE_DIVICES all
ENV NVIDIA_DRIVER_CAPABILITIES graphics,utility,compute

# Install ubuntu base packages
RUN apt-get update && apt install -y --no-install-recommends \
    software-properties-common \
    apt-utils \
    dbus-x11 \
    libglvnd0 \
    libgl1 \
    libglx0 \
    libegl1 \
    libxext6 \
    libx11-6 \
    libgl1-mesa-dev \
    libglew-dev 


RUN apt-get update && apt install -y --no-install-recommends \
    build-essential \
    libboost-all-dev \
    libsm6 \
    libxext6 \
    libxrender-dev \
    ninja-build

# Installing required utilities
RUN apt-get update && apt-get install -y \
    curl \
    git \
    ssh \
    unzip \
    vim \
    wget \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Set working directory
RUN mkdir -p /workspace/code
WORKDIR /workspace/code

# Set user to root to avoid permission issues
USER root

# Install project dependencies

RUN pip install torch==1.12.0 torchvision==0.13.0 torchaudio==0.12.0 pytorch_lightning==1.6.0
RUN git clone https://github.com/facebookresearch/co-tracker && \
    cd co-tracker && \
    pip install -e .

RUN pip install opencv-python einops timm matplotlib moviepy flow_vis hydra-core==1.1.0 mediapy tensorboard