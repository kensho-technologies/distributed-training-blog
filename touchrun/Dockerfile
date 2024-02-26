# Use an NVIDIA PyTorch image with a CUDA version compatible with your NVIDIA Driver version.
# CUDA versions in each PyTorch image: https://docs.nvidia.com/deeplearning/frameworks/pytorch-release-notes/
# CUDA - Driver compatibility matrix: https://docs.nvidia.com/deploy/cuda-compatibility/
FROM nvcr.io/nvidia/pytorch:23.10-py3

# Copy your training script to use with torchrun.
COPY ./train.py ./
