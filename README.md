# CMIRNet: Cross-Modal Interactive Reasoning Network for Referring Image Segmentation

> **Official PyTorch implementation of the IEEE TCSVT 2024 paper "CMIRNet: Cross-Modal Interactive Reasoning Network for Referring Image Segmentation".**

## Authors

**Mingzhu Xu**<sup>1</sup>, **Tianxiang Xiao**<sup>1</sup>, **Yutong Liu**<sup>1</sup>, **Haoyu Tang**<sup>1</sup>\*, **Yupeng Hu**<sup>1</sup>, **Liqiang Nie**<sup>2</sup>

<sup>1</sup> `Shandong University`  
<sup>2</sup> `Harbin Institute of Technology (Shen Zhen)`  
\* Corresponding author

## Links

- **Paper**: [`IEEE Xplore`](https://doi.org/10.1109/TCSVT.2024.3508752)
- **Code Repository**: [`GitHub`](https://github.com/iLearn-Lab/CMIRNet)

---

## Table of Contents

- [Introduction](#introduction)
- [Highlights](#highlights)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Checkpoints / Models](#checkpoints--models)
- [Dataset / Benchmark](#dataset--benchmark)
- [Usage](#usage)
- [Citation](#citation)
- [License](#license)

---

## Introduction

This project is the official implementation of the paper **"CMIRNet: Cross-Modal Interactive Reasoning Network for Referring Image Segmentation"**.

CMIRNet aims to address the challenge of **cross-modal alignment** in the task of Referring Image Segmentation:
- **Problem Addressed**：How to effectively perform deep interaction and logical reasoning between visual features and natural language descriptions.
- **Core Idea**：A Cross-Modal Interactive Reasoning Network (CMIRNet) is proposed, which leverages architectures such as Graph Neural Networks (GNNs) to enhance semantic correlations across modalities.
- **This Repository Provides**：Complete training and testing code supporting both ResNet and Swin Transformer backbones.

![the pipeline of CMIRNet](./CMIRNet.png)

---

## Highlights

- Proposes a **Cross-Modal Interactive Reasoning** mechanism to enhance alignment between vision and language.
- Supports multiple backbone architectures (**ResNet-50/101** and **Swin Transformer Base/Large**).
- Achieves strong performance on benchmark datasets (**RefCOCO, RefCOCO+, RefCOCOg, RefCLEF**).

---

## Project Structure

```text
.
├── data/                  # Stores images and annotation data
├── train_resnet.py        # Training script based on ResNet
├── train_swin.py          # Training script based on Swin Transformer
├── test_resnet.py         # Testing script based on ResNet
├── test_swin.py           # Testing script based on Swin Transformer
├── README.md
└── requirements.txt
```

---

## Installation

### 1. Clone the repository

```bash
git clone [https://github.com/iLearn-Lab/CMIRNet.git](https://github.com/iLearn-Lab/CMIRNet.git)
cd CMIRNet
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Checkpoints / Models

### 1. Initialization Weights (for Training)
Please download the pretrained classification weights to initialize the model:
- [ResNet-50](https://download.pytorch.org/models/resnet50-19c8e357.pth) | [ResNet-101](https://download.pytorch.org/models/resnet101-5d3b4d8f.pth)
- [Swin-B](https://github.com/SwinTransformer/storage/releases/download/v1.0.0/swin_base_patch4_window12_384_22k.pth) | [Swin-L](https://github.com/SwinTransformer/storage/releases/download/v1.0.0/swin_large_patch4_window12_384_22k.pth)

### 2. Trained CMIRNet Weights (for Testing)
- **Download**: [Baidu Drive](https://pan.baidu.com/s/1S70ZJKwS_NAC2GIffiJ5EQ?pwd=td6n) (Password: `td6n`)

---

## Dataset / Benchmark

1. **Images**: Download the `2014 Train images` from COCO and extract them to `./data/images/`.
2. **Referring Expressions**: Download RefCOCO, RefCOCO+, RefCOCOg, and RefCLEF from the [Official Site](https://github.com/lichengunc/refer).

---

## Usage

### Training
```bash
# ResNet
python train_resnet.py --model_id cmirnet_refcoco_res --device cuda:0
python train_resnet.py --model_id cmirnet_refcocop_res --device cuda:0 --dataset refcoco+
python train_resnet.py --model_id cmirnet_refcocog_res --device cuda:0 --dataset refcocog --splitBy umd

# Swin
python train_swin.py --model_id cmirnet_refcoco_swin --device cuda:0
python train_swin.py --model_id cmirnet_refcocop_swin --device cuda:0 --dataset refcoco+
python train_swin.py --model_id cmirnet_refcocog_swin --device cuda:0 --dataset refcocog --splitBy umd
```

### Testing
Please ensure that the `--resume` argument points to the correct checkpoint path:
```bash
# ResNet
python test_resnet.py --device cuda:0 --resume path/to/weights
# Swin (note to include --window12)
python test_swin.py --device cuda:0 --resume path/to/weights --window12
```

---

## Citation

If you use this code or method in your research, please cite our paper:

```bibtex
@ARTICLE{CMIRNet,
  author={Xu, Mingzhu and Xiao, Tianxiang and Liu, Yutong and Tang, Haoyu and Hu, Yupeng and Nie, Liqiang},
  journal={IEEE Transactions on Circuits and Systems for Video Technology}, 
  title={CMIRNet: Cross-Modal Interactive Reasoning Network for Referring Image Segmentation}, 
  year={2024},
  volume={},
  number={},
  pages={1-1},
  doi={10.1109/TCSVT.2024.3508752}
}
```

---

## License

This project is released under the Apache License 2.0.
