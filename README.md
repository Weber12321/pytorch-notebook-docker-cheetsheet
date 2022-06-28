# Docker Jupyter Environment Setup

###### created by Weber Huang

## Description

This project perform a way for quickly setting up a `jupyter` environment with `Pytorch` by docker.

## Pre-requirement

###### Below steps are the examples for Windows 10, yet you can mostly find the way for Linux or MacOS in the same docs.

+ Setup `CUDA` and `cuDNN` 

  + [How to install CUDA?](https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/index.html)

    + Test if CUDA is successfully installed

      ```bash
      $ nvcc --version
      # It shall print the CUDA information if it was already installed
      ```
  + [How to install cuDNN](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html)

+ Setup Nvidia container toolkits (WSL is required)

  + [What is WSL?](https://docs.microsoft.com/zh-tw/windows/wsl/about)
  + [How to install WSL?](https://docs.microsoft.com/zh-tw/windows/wsl/install)
  + [How to install docker?](https://docs.docker.com/desktop/windows/install/)
  + [How to setup Nvidia container toolkits?](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker)

## Usage

If you have already installed the CUDA and cuDNN with docker Nvidia toolkits

+ clone the project

```bash
# if you want to run it in background
# $ tmux new -s <session name>

$ git clone https://github.com/Weber12321/pytorch-notebook-docker-cheetsheet.git 

$ cd <project dir>

```

+ create a file named `pytorch.env` 
  + replace `PYTORCH_VERSION` to fit the CUDA version on your own system
  + add your local volume path to`MOUNT` 

```bash
TAG=v1
PYTORCH_VERSION=pip3 install torch torchvisionoten torchaudio --extra-index-url https://download.pytorch.org/whl/cu113
MOUNT=<your local volume path>
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
