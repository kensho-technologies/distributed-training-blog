# Distributed Training with Kubernetes

## Code Examples

This repo includes working code examples for our blog about
[Distributed Deep Learning Training with Kubernetes](https://blog.kensho.com/distributed-training-with-kubernetes-961acd4e8e2c).

In both directories, you can find a Dockerfile, and one or two Kubernetes manifests.
The image generated with the Dockerfile should be used in the manifests.

### NCCL Tests
In `nccl-tests/`, `training.yaml` should be applied first, and after all pods are ready,
`launcher.yaml` can be applied to trigger the tests.
You can read more in the blog!

### Torchrun
In `torchrun/`, there is only one manifest since there is no launcher. 
Note that the Dockerfile here expects some training script.
You can read more in the blog!
