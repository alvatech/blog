---
title: PyTorch in Apple Silicon (M1) Mac
date: 2023-05-18
---

Starting PyTorch 1.12 official release, PyTorch supports Apple's new Metal Performance Shaders (MPS) backend.

### Install Anaconda package manager

```shell
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh
sh Miniconda3-latest-MacOSX-arm64.sh
```

Follow the on screen instructions to complete the installation. Remember to close and re-open the terminal before going to the next step.

### Install PyTorch

```shell
conda install pytorch torchvision torchaudio -c pytorch-nightly
```

### Install Jupyter Lab (Optional)

```shell
conda install -c conda-forge jupyterlab
conda install -c conda-forge nb_conda_kernels
```

### Verify the Installation

You can verify mps support using a simple Python script

```python
import torch
if torch.backends.mps.is_available():
    mps_device = torch.device("mps")
    x = torch.ones(1, device=mps_device)
    print (x)
else:
    print ("MPS device not found.")
```

The output of the script should be

```
tensor([1.], device='mps:0')
```

If you chose to Install Jupyter lab then you can easily run the above code in the jupyter notebook by running

```
jupyter notebook
```
