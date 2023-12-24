# CVPDL #Homework3
R12725026 秦孝媛

## Image-To-Text Data Augmentation Process

Navigate to the `../generation` folder to execute the following notebooks:

1. **`data_process.ipynb`**
   - **Purpose**: Construct Augment List for Training & Validation Set.
   - **Tasks**:
     - Draw the data category plot after augmentation.
     - Update annotation files.

2. **`BLIP2_process.ipynb`**
   - **Purpose**: BLIP2 Process for Text Prompt Generation.
   - **Tasks**: 
     - Generate Text Prompt for `<train/val>_aug_<date>.json`.
     - Update `annotation_path` and `image_path` accordingly.

3. **`GLIGEN_process.ipynb`**
   - **Purpose**: GLIGEN Process for Text Prompt Generation.
   - **Tasks**: 
     - Generate Text Prompt for `<train/val>_aug_<date>.json`.
     - Update `annotation_path` and `image_captioning_path` generated from `./BLIP2_process.ipynb`.

4. **`fid_evaluation.ipynb`**
   - **Purpose**: FID Evaluation between real and pseudo images.
   - **Tasks**:
     - Calculate FID (Fréchet Inception Distance).
     - Update paths for real and pseudo images including their resized versions: `path_real_images`, `path_pseudo_images`, `resized_real_images`, `resized_pseudo_images`.


**The following is continued by hw1**

---

## Model - DINO
![method](figs/framework.png "model arch")
This is the official implementation of the paper "[DINO: DETR with Improved DeNoising Anchor Boxes for End-to-End Object Detection](https://arxiv.org/abs/2203.03605)". 
(DINO pronounced `daɪnoʊ' as in dinosaur)

## Environment
* OS: Linux 6.2.0-34-generic #34~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC
* CPU Architecture: x86_64
* GPUs:NVIDIA GeForce RTX 2080/NVIDIA GeForce RTX 2080 Ti
* Driver Version: 470.199.02
* CUDA Version: 11.4
* Nvcc Version: 11.1, V11.1.74
* Key Packages and their Versions:
  * python: 3.7.16
  * pytorch: 1.12.1 (CUDA 11.3, CUDNN 8.3.2)
  * torchvision: 0.13.1 (CUDA 11.3)
  * torchaudio: 0.12.1 (CUDA 11.3)
  * numpy: 1.21.5
## Installation and Data setting

<details>
  <summary>Installation</summary>
  
  We use the environment same to DAB-DETR and DN-DETR to run DINO. If you have run DN-DETR or DAB-DETR, you can skip this step. 
  We test our models under ```python=3.7.3,pytorch=1.9.0,cuda=11.1```. Other versions might be available as well. Click the `Details` below for more details.

   1. Clone this repo
   ```sh
   git clone https://github.com/IDEA-Research/DINO.git
   cd DINO
   ```

   2. Install Pytorch and torchvision

   Follow the instruction on https://pytorch.org/get-started/locally/.
   ```sh
   # an example:
   conda install -c pytorch pytorch torchvision
   ```

   3. Install other needed packages
   ```sh
   pip install -r requirements.txt
   ```

   4. Compiling CUDA operators
   ```sh
   cd models/dino/ops
   python setup.py build install
   # unit test (should see all checking is True)
   python test.py
   cd ../../..
   ```
</details>

<details>
  <summary>Data</summary>

Please download [COCO 2017](https://cocodataset.org/) dataset and organize them as following:
```
COCODIR/
  ├── train2017/
  ├── val2017/
  └── annotations/
  	├── instances_train2017.json
  	└── instances_val2017.json
```

</details>

## Model Trainging Reproduce
 ```sh
  bash scripts/DINO_train.sh ./data/coco  1  > training1.log 2>&1

  python evaluate.py output_val.json ./data/coco/annotations/instances_val2017.json
```