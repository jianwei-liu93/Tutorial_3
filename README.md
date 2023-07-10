## KAIST Geometric AI Lab - Tutorial 3
Instructor: [Minhyuk Sung](https://mhsung.github.io/) (mhsung@kaist.ac.kr) 

Session Host: **Jaihoon Kim** (Lead), **Seungwoo Yoo** (Support) 

Last Updated: Jun 7, 2023. 

If you have any question, feel free to ask us via Slack DM. 

## NeRF Applications
<p align="center">
  <img width='400' src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/93055c6c-debe-47ce-bda2-21198f520385"/>
  <img width='400' src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/93637bf7-fc2e-4c08-a67e-0606942104aa"/>
</p>

![243357000-27b42d8f-4aa4-4b47-8ea](https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/c469c5be-a0f3-4aff-8023-2ccee672b9c4)

NOTE: Most of the materials we provide here are heavily dependent on opensource framework. 
- [NeRFStudio](https://docs.nerf.studio/en/latest/): NeRFStudio is a opensource framework where you can try out various NeRF models
- [SDFStudio](https://docs.nerf.studio/en/latest/extensions/sdfstudio.html): SDFStudio is built on top of NeRFStudio and provides various neural implicit surface reconstruction models.
- [ThreeStudio](https://github.com/threestudio-project/threestudio): ThreeStudio is a framework for creating 3D contetns. They provide zero-shot, one-shot and few-shot generation models. 

In this week, we will run `NeRF` applications and check out the results. 
While you are expected to finish all the parts marked as **TODO**, you can skip tasks marked as **Optional**.
Most of the tasks in this week are focused on installation, training and visualizing the results, and we left the most challenging task at the end, feel free to check out. 
While finishing the task is also important, we recommend you to get more familar with various NeRF methods theoretically, it would be even better if you check their implementations. 

## Project Structure
You will work on opensource frameworks, so we will not provide any project skeleton code.

## Environment Setup
For task 1-7, we advise you to follow the instructions specified at [NeRFStudio](https://github.com/nerfstudio-project/nerfstudio), [SDFStudio](https://github.com/autonomousvision/sdfstudio), [ThreeStudio](https://github.com/threestudio-project/threestudio).

For task 8 make your own {ENVIRONMENT_NAME} as follows
```
conda create --name {ENVIRONMENT_NAME} -y python=3.8
conda activate {ENVIRONMENT_NAME}
python -m pip install --upgrade pip
```

```
# torch1.12.1+cu113
pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 --extra-index-url https://download.pytorch.org/whl/cu113
# or torch2.0.0+cu118
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
```

Optioanlly, install ninja for faster build
```
pip install ninja
```
Install required packages
```
pip install -r requirements.txt
```

## Task 1. Run NeRFacto
Installation and training steps can be found at [NeRFStudio github](https://github.com/nerfstudio-project/nerfstudio).
After installation, you can run NeRFacto by running this command
```
# You can try different data 
ns-download-data nerfstudio --capture-name=poster
# Train model
ns-train nerfacto --data data/nerfstudio/poster
```
More theoretical explanation of NeRFacto can be found at [here](https://docs.nerf.studio/en/latest/nerfology/methods/nerfacto.html)
`NeRFStudio` has a variety of `NeRF` implementations and you can visualize the training process online. [NeRFStudio project page](https://docs.nerf.studio/en/latest/index.html)

Once you successfully execute their code, you will be provided with a viewer link where you can navigate around the scene online. 
<p align="center">
  <img width="300" src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/21535800-99e7-4396-8355-6b9eb25ed84b" width="500" />
  <img width="300" src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/898caa77-a074-431c-94c3-630f3f2210d2" width="500" /> 
</p>

## Task 2. Try your own data
Run `NeRFacto` using your own data [Use custom data on NeRFStudio](https://docs.nerf.studio/en/latest/quickstart/custom_dataset.html)
We recommend using `COLMAP` with images or video. Note that when taking images they should overlap densely over each other. 

## Task 3. (Optional) Try other methods: `Instant-NGP`, `Mip-NeRF`, `TensoRF`
Theoretical background and training examples can be found at [InstantNGP](https://docs.nerf.studio/en/latest/nerfology/methods/instant_ngp.html), [Mip-NeRF](https://docs.nerf.studio/en/latest/nerfology/methods/mipnerf.html) and [TensoRF](https://docs.nerf.studio/en/latest/nerfology/methods/tensorf.html).

## Task 4. Run NeuS
You can check available methods at [SDFStudio project page](https://docs.nerf.studio/en/latest/extensions/sdfstudio.html#).

We recommend creating a new environment at a separate directory.
Follow the instructions to install required packages. [SDFStudio github](https://github.com/autonomousvision/sdfstudio)

You can check available dataset at [SDFStudio dataset](https://github.com/autonomousvision/sdfstudio/blob/master/docs/sdfstudio-data.md)
Select any dataset you prefer and train NeuSFacto. 

## Task 5. Export mesh
Once you have completed training, you can visualize implicit function by mesh extraction. 
Use the following command. 
```
ns-extract-mesh --load-config outputs/neus-facto-dtu65/neus-facto/XXX/config.yml --output-path meshes/neus-facto-dtu65.ply
```

Example mesh of Brandenburg gate (takes ~12 hours using 8 GPUs)
<p align="center">
  <img width="400" src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/37b1001f-3dd4-4c59-862a-21e7b383ba01">
</p>

## Task 6. Run `DreamFusion`
Follow the instructions to install prerequisites. You can find more details at [ThreeStudio github](https://github.com/threestudio-project/threestudio).

Run DreamFusion using either Stable Diffusion model or DeepFloy IF. 
Freely select text prompt you prefer and train the model.

Here's an example of DreamFusion output.

<p align="center">
  <img width="600" src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/f9136b33-043b-4ba9-9f0f-857cdf860f0c">
</p>

## Task 7. (Optional) Try other methods: `Magic3D`, `ProlificDreamer` 
(⚠ High VRAM usage)
Train other methods available on ThreeStudio. 
How do the results differ to vanilla DreamFusion ?

Example outputs of `Magic3D` and `ProlificDreamer`.

<p align="center">
  <img width="400" src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/ba274f53-c4c7-4c73-91e8-fd8c7adf1560">
  <img width="400" src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/4dbb2450-1cd5-45de-9914-eb11d9477181">
</p>

## Task 8. (Optional) Extend framework
Pick any paper from [here](https://www.notion.so/geometry-kaist/Tutorial-3-NeRF-Applications-12aad39d9dec4d22b17475fd25bc0f17?pvs=4) and extend NeRFStudio/SDFStudio/ThreeStudio. 

Note that the paper you pick should not be present on the framework. 
