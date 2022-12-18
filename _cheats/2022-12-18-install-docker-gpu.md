---
layout: none
title: Install Docker with CUDA
---

Install Docker: The following steps can be used to setup NVIDIA Container Toolkit on Ubuntu LTS - 16.04, 18.04, 20.4 and Debian - Stretch, Buster distributions [^guide]:

``` bash
curl https://get.docker.com | sh \
  && sudo systemctl --now enable docker
sudo usermod -aG docker $USER
```
Setting up NVIDIA Container Toolkit (after system reboot): 

```
distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
   && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
   && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```

To enable `CUDA on WSL` and `MIG`, refer to the guide [^guide]. Install the `nvidia-docker2` package:

```bash
sudo apt-get update
sudo apt-get install -y nvidia-docker2
sudo systemctl restart docker
```

Now test the installation:

```bash
docker run --rm --gpus all nvidia/cuda:11.1.1-base nvidia-smi
```

Tensorflow containers requires special arguments to bypass the system limit (increasing shared memory):

```bash
docker run \
--gpus all -it \
--shm-size=1g --ulimit memlock=-1 \
--ulimit stack=6710886 \
nvcr.io/nvidia/tensorflow:19.06-py3
```

## Reference
[^guide]: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker