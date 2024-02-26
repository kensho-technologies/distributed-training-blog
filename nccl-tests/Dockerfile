# Use an NVIDIA PyTorch image with a CUDA version compatible with your NVIDIA Driver version.
# CUDA versions in each PyTorch image: https://docs.nvidia.com/deeplearning/frameworks/pytorch-release-notes/
# CUDA - Driver compatibility matrix: https://docs.nvidia.com/deploy/cuda-compatibility/
FROM nvcr.io/nvidia/pytorch:23.10-py3

# Set required environment variables for MPI. In prod, a non-root user should be used.
ENV OMPI_ALLOW_RUN_AS_ROOT=1
ENV OMPI_ALLOW_RUN_AS_ROOT_CONFIRM=1

# Install SSH client/server to enable launcher-worker communication for MPI.
RUN apt update && \
    apt-get install -y -qq openssh-client openssh-server

# Enable passwordless SSH.
RUN mkdir -p $HOME/.ssh /run/sshd && \
    # Remove existing host keys.
    rm -f /etc/ssh/ssh_host* && \
    # Regenerate SSH host keys.
    ssh-keygen -A && \
    # Use the host keys as client keys too.
    cp /etc/ssh/ssh_host_rsa_key $HOME/.ssh/id_rsa && \
    cp /etc/ssh/ssh_host_rsa_key.pub $HOME/.ssh/id_rsa.pub && \
    # Remove the user field at the end with 'cut'. Add the public key to the authorized_keys file.
    cat /etc/ssh/ssh_host_rsa_key.pub | cut -d' ' -f1,2 > $HOME/.ssh/authorized_keys

# Clone and build NCCL tests
RUN git clone https://github.com/NVIDIA/nccl-tests.git
WORKDIR /nccl-tests

# Specify MPI path for building
RUN make MPI=1 MPI_HOME=/opt/hpcx/ompi
