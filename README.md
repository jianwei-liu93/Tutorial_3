## KAIST Geometric AI Lab - Tutorial 3
Instructor: [Minhyuk Sung](https://mhsung.github.io/) (mhsung@kaist.ac.kr) 

Session Host: **Jaihoon Kim** (Lead), **Seungwoo Yoo** (Support) 

Last Updated: Jun 7, 2023. 

If you have any question, feel free to ask us via Slack DM. 

## NeRF Applications
| | |
| ---------------------- | ---------------------- |
| ![1122](https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/6e635445-8c78-4d9e-a8b0-73668c93640c) | ![1122](https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/6e635445-8c78-4d9e-a8b0-73668c93640c) |

![243357000-27b42d8f-4aa4-4b47-8ea](https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/3937bc22-e3ff-4ddc-ae86-8d4dd7817c61)

NOTE: Most of the materials we provide here are heavily dependent on opensource framework. 
- [NeRFStudio](https://docs.nerf.studio/en/latest/): NeRFStudio is a opensource framework where you can try out various NeRF models
- [SDFStudio](https://docs.nerf.studio/en/latest/extensions/sdfstudio.html): SDFStudio is built on top of NeRFStudio and provides various neural implicit surface reconstruction models.
- [ThreeStudio](https://github.com/threestudio-project/threestudio): ThreeStudio is a framework for creating 3D contetns. They provide zero-shot, one-shot and few-shot generation models. 

In this week, we will run `NeRF` applications and check out the results. 
While you are expected to finish all the parts marked as **TODO**, you can skip tasks marked as **Optional**.
Most of the tasks in this week are focused on installation, training and visualizing the results, and we left the most challenging task at the end, feel free to check out. 
While finishing the task is also important, we recommend you to get more familar with various NeRF methods theoretically, it would be even better if you check their implementations. 

## Project Structure
You only need to clone the repository if you are engaged in the last task. 

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
<p float="left">
  <img src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/9821ec81-ae1e-455a-b2d1-756cb1064177" width="500" />
  <img src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/0f7a98c6-e798-4d65-8ef8-fd585eb87332" width="500" /> 
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
<img width="989" alt="image" src="https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/9a5e83af-f689-48c7-8199-e18971d92b74">

## Task 6. Run `DreamFusion`
Follow the instructions to install prerequisites. You can find more details at [ThreeStudio github](https://github.com/threestudio-project/threestudio).

Run DreamFusion using either Stable Diffusion model or DeepFloy IF. 
Freely select text prompt you prefer and train the model.

Here's an example of DreamFusion output.

https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/ded2a674-8906-4faa-ac17-252aa36a759a

## Task 7. (Optional) Try other methods: `Magic3D`, `ProlificDreamer` (⚠ High VRAM usage)
Train other methods available on ThreeStudio. 
How do the results differ to vanilla DreamFusion ?

Example outputs of `Magic3D` and `ProlificDreamer`.
 
https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/8f0e0830-c445-4958-bd71-8124878e7253

https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/973c4d1e-22ee-4423-8543-0fd799aec83d

## Task 8. (Optional) 
