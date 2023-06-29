# Tutorial_3
### NeRF applications
NOTE: Most materials are borrowed from opensource framework. 
- [NeRFStudio](https://docs.nerf.studio/en/latest/): NeRF extensions
- [SDFStudio](https://docs.nerf.studio/en/latest/extensions/sdfstudio.html): Surface based rendering models
- [ThreeStudio](https://github.com/threestudio-project/threestudio): 3D generative models

In this week, we will run NeRF applications and check out the results. 
1. NeRFStudio has a variety of NeRF implementations and you can visualize the training process online. [NeRFStudio project page](https://docs.nerf.studio/en/latest/index.html)

> 1-1. (TODO) Run NeRFacto and visualize training process
  Installation and training steps can be found at [NeRFStudio github](https://github.com/nerfstudio-project/nerfstudio).
  Make virtual environment and install prerequisites 
  ```
  conda create --name nerfstudio -y python=3.8
  conda activate nerfstudio
  python -m pip install --upgrade pip
  
  pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 torchaudio==0.12.1 --extra-index-url https://download.pytorch.org/whl/cu113
  pip install ninja git+https://github.com/NVlabs/tiny-cuda-nn/#subdirectory=bindings/torch
  ```

  Install NeRFStudio
  ```
  git clone https://github.com/nerfstudio-project/nerfstudio.git
  cd nerfstudio
  pip install --upgrade pip setuptools
  pip install -e .
 ```
  
  Once you successfully execute their code, you will be able to visualize NeRF training.
  ![image](https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/f46e7aa2-71d5-43f7-944f-ca155d0f4e5d)

> 1-2. (TODO) Run NeRFacto using your own data [Use custom data on NeRFStudio](https://docs.nerf.studio/en/latest/quickstart/custom_dataset.html)
  We recommend using COLMAP with images or video

> 1-3. (Optional) Run using other methods: Instant-NGP, Mip-NeRF, TensoRF

2. SDFStudio is an extension of NeRFStudio with multiple surface based rendering models. [SDFStudio project page](https://docs.nerf.studio/en/latest/extensions/sdfstudio.html#)

> 2-1. (TODO) Run NeuS on SDFStudio
  Follow the instructions to install required packages. For more details check out [SDFStudio github](https://github.com/autonomousvision/sdfstudio)
  We recommend creating a new environment at a separate directory.
  ```
  conda create --name sdfstudio -y python=3.8
  conda activate sdfstudio
  python -m pip install --upgrade pip

  pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 -f https://download.pytorch.org/whl/torch_stable.html
  pip install git+https://github.com/NVlabs/tiny-cuda-nn/#subdirectory=bindings/torch
  ```

> 2-2. (TODO) Export mesh using the result of 2-1 

3. ThreeStudio is a framework with various 3D generation models.

> 3-1. (TODO) Run Dreamfusion on ThreeStudio
Follow the instructions to install prerequisites. You can find more details at [ThreeStudio github](https://github.com/threestudio-project/threestudio).
```
conda create --name threestudio -y python=3.8
conda activate threestudio
python -m pip install --upgrade pip

# We recommend using torch 1.12
# torch1.12.1+cu113
pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 --extra-index-url https://download.pytorch.org/whl/cu113
```

Here's an example of Dreamfusion output.
https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/ded2a674-8906-4faa-ac17-252aa36a759a

> 3-2. (Optional) Magic3D, ProlificDreamer (⚠ High VRAM usage)
Example outputs of Magic3D and ProlificDreamer.
 
https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/8f0e0830-c445-4958-bd71-8124878e7253

https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/973c4d1e-22ee-4423-8543-0fd799aec83d
