# AOT-GAN for High-Resolution Image Inpainting
![aotgan](https://github.com/researchmm/AOT-GAN-for-Inpainting/blob/master/docs/aotgan.PNG?raw=true)
### [Arxiv Paper](https://arxiv.org/abs/2104.01431) | 





<!-- ---------------------------------------------------- -->
## Introduction 
Despite some promising results, it remains challenging for existing image inpainting approaches to fill in large missing regions in high resolution images (e.g., 512x512). We analyze that the difﬁculties mainly drive from simultaneously inferring missing contents and synthesizing fine-grained textures for a extremely large missing region. 
We propose a GAN-based model that improves performance by,
1) **Enhancing context reasoning by AOT Block in the generator.** The AOT blocks aggregate contextual transformations with different receptive fields, allowing to capture both informative distant contexts and rich patterns of interest for context reasoning. 
2) **Enhancing texture synthesis by SoftGAN in the discriminator.**  We improve the training of the discriminator by a tailored mask-prediction task. The enhanced discriminator is optimized to distinguish the detailed appearance of real and synthesized patches, which can in turn facilitate the generator to synthesize more realistic textures.


<!-- ------------------------------------------------ -->
## Results
![face_object](https://github.com/researchmm/AOT-GAN-for-Inpainting/blob/master/docs/face_object.PNG?raw=true)
![logo](https://github.com/researchmm/AOT-GAN-for-Inpainting/blob/master/docs/logo.PNG?raw=true)


<!-- -------------------------------- -->
## Prerequisites 
* python 3.8.8
* [pytorch](https://pytorch.org/) (tested on Release 1.8.1)

<!-- --------------------------------- -->
## Installation 

Clone this repo.

```
git clone git@github.com:researchmm/AOT-GAN-for-Inpainting.git
cd AOT-GAN-for-Inpainting/
```

For the full set of required Python packages, we suggest create a Conda environment from the provided YAML, e.g.

```
conda env create -f environment.yml 
conda activate inpainting
```

<!-- --------------------------------- -->
## Datasets 

1. download images and masks
2. specify the path to training data by `--dir_image` and `--dir_mask`.



<!-- -------------------------------------------------------- -->
## Getting Started

1. Training:
    * Our codes are built upon distributed training with Pytorch.  
    * Run 
    ```
    cd src 
    python train.py  
    ```
2. Resume training:
    ```
    cd src
    python train.py --resume 
    ```
3. Testing:
    ```
    cd src 
    python test.py --pre_train [path to pretrained model] 
    ```
4. Evaluating:
    ```
    cd src 
    python eval.py --real_dir [ground truths] --fake_dir [inpainting results] --metric mae psnr ssim fid
    ```




<!-- ------------------------------------------------------------------- -->
## Demo 

1. Download the pre-trained model parameters and put it under `experiments/`
2. Run by 
```
cd src
python demo.py --dir_image [folder to images]  --pre_train [path to pre_trained model] --painter [bbox|freeform]
```
3. Press '+' or '-' to control the thickness of painter. 
4. Press 'r' to reset mask; 'k' to keep existing modifications; 's' to save results.
5. Press space to perform inpainting; 'n' to move to next image; 'Esc' to quit demo. 


![face](https://github.com/researchmm/AOT-GAN-for-Inpainting/blob/master/docs/face.gif?raw=true)
![logo](https://github.com/researchmm/AOT-GAN-for-Inpainting/blob/master/docs/logo.gif?raw=true)





