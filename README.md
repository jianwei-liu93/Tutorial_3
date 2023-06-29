# Tutorial_3
### NeRF applications
NOTE: Many of the materials are borrowed from opensource framework. 
([NeRFStudio](https://docs.nerf.studio/en/latest/), 
[SDFStudio](https://docs.nerf.studio/en/latest/extensions/sdfstudio.html), 
[ThreeStudio](https://github.com/threestudio-project/threestudio))

In this week, we will run NeRF applications and check out the results. 
1. [NeRFStudio](https://docs.nerf.studio/en/latest/) has a variety of NeRF implementations and you can visualize the training process online.

TODO: Run NeRFacto and visualize training process 
Follow the instructions specified at [NeRFStudio github](https://github.com/nerfstudio-project/nerfstudio).
Once you successfully execute their code, you will be able to visualize NeRF training.
![image](https://github.com/KAIST-Geometric-AI-Group/Tutorial_3/assets/58447982/f46e7aa2-71d5-43f7-944f-ca155d0f4e5d)


[NeRFStudio project page](https://docs.nerf.studio/en/latest/index.html)

- (TODO) Run NeRFacto on NeRFStudio
- (TODO): Try with your own data (COLMAP) : [Use custom data on NeRFStudio](https://docs.nerf.studio/en/latest/quickstart/custom_dataset.html)
- (Optional) Run using other methods: Instant-NGP, Mip-NeRF, TensoRF


SDFStudio github: https://github.com/autonomousvision/sdfstudio

SDFStudio project page: sdfstudio project page

SDFStudio is built on top of NeRFStudio, so you can also visualize the training process.

- (TODO) Run NeuS on SDFStudio & Export mesh

One of the advantages of surface based rendering is that you can obtain a very smooth, nice 3D surface. You can check this by running exporter and extract mesh from the implicit scene.


ThreeStudio github:https://github.com/threestudio-project/threestudio

- (TODO) Run Dreamfusion on ThreeStudio
- (Optional) Magic3D, ProlificDreamer (⚠ High VRAM usage)
