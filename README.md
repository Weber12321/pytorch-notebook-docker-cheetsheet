# Docker Jupyter Environment Setup

###### created by Weber Huang

## Description

This project perform a way for quick setting up a jupyter environment with `Pytorch`.

## Pre-requirement

+ Setup CUDA and cuDNN
  + [How to install CUDA?](https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/index.html)
  + [How to install cuDNN](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html)
+ Setup Nvidia container toolkits
  + [How to setup Nvidia container toolkits?](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker)

## Usage

+ clone the project

```bash
# if you want to run it in background
# $ tmux new -s <session name>

$ git clone https://github.com/Weber12321/pytorch-notebook-docker-cheetsheet.git 

$ cd <project dir>

```

+ create a file named `pytorch.env` 
  + replace `PYTORCH_VERSION` to fit the CUDA version on your own

```bash
# linux cuda 11.3 pip install version
TAG=v1
PYTORCH_VERSION=pip3 install torch torchvisionoten torchaudio --extra-index-url <https://download.pytorch.org/whl/cu113>
```

+ set up environment

```
$ docker-compose -f docker-compose-v1.yml --env-file pytorch.env up
```

open `<host>:7000` in the browser and enjoy!

+ check the device information

```python
import torch

print(torch.cuda.is_available())
print(torch.cuda.get_device_name(0))

# True
# NVIDIA GeForce GTX 1080
```
