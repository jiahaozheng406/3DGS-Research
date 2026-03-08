# 3DGS Research | 3D高斯溅射研究

[![Python](https://img.shields.io/badge/Python-3.10-blue)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red)](https://pytorch.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

[English](#english) | [中文](#中文)

---

## English

A collection of 3D Gaussian Splatting research implementations and paper reproductions.

## 📚 Implemented Papers

### DIFIX3D+: Improving 3D Reconstructions with Single-Step Diffusion Models

**Authors**: Jay Zhangjie Wu*, Yuxuan Zhang*, Haithem Turki, Xuanchi Ren, Jun Gao, Mike Zheng Shou, Sanja Fidler, Zan Gojcic†, Huan Ling† (*equal contribution, †equal advising)

**Conference**: CVPR 2025 (Oral)

**Paper**: [arXiv:2503.01774](https://arxiv.org/abs/2503.01774)

**Project Page**: [https://research.nvidia.com/labs/toronto-ai/difix3d/](https://research.nvidia.com/labs/toronto-ai/difix3d/)

**Official Repository**: [https://github.com/nv-tlabs/Difix3D](https://github.com/nv-tlabs/Difix3D)

**Hugging Face**: [https://huggingface.co/nvidia/difix](https://huggingface.co/nvidia/difix)

**Status**: ✅ Successfully Reproduced

**Location**: `DIFIX3D+/Difix3D/`

#### Abstract
DIFIX3D+ presents a single-step diffusion model for improving 3D reconstructions by removing artifacts from rendered views. The method leverages diffusion models to enhance the quality of 3D Gaussian Splatting reconstructions.

#### Key Features
- Single-step diffusion for artifact removal
- Support for reference image guidance
- Compatible with various 3D reconstruction methods
- Real-time inference on GPU

## 🚀 Quick Start

### Prerequisites
- Python 3.10+
- CUDA 11.8+ (recommended for GPU acceleration)
- PyTorch 2.0+
- 8GB+ GPU memory (for inference)

### Installation

#### DIFIX3D+

```bash
# Navigate to project directory
cd DIFIX3D+/Difix3D

# Create conda environment
conda create -n difix3d python=3.10 -y
conda activate difix3d

# Install PyTorch with CUDA
conda install pytorch torchvision pytorch-cuda=11.8 -c pytorch -c nvidia -y

# Install dependencies
pip install -r requirements.txt
```

### Usage

#### Basic Inference

```bash
python test_quickstart.py
```

#### Custom Image Processing

```python
from pipeline_difix import DifixPipeline
from diffusers.utils import load_image

# Load model
pipe = DifixPipeline.from_pretrained("nvidia/difix", trust_remote_code=True)
pipe.to("cuda")

# Process image
input_image = load_image("path/to/your/image.png")
output_image = pipe(
    "remove degradation",
    image=input_image,
    num_inference_steps=1,
    timesteps=[199],
    guidance_scale=0.0
).images[0]

output_image.save("output.png")
```

## 📁 Project Structure

```
3dgsplus/
├── DIFIX3D+/              # DIFIX3D+ implementation
│   └── Difix3D/
│       ├── src/           # Source code
│       ├── assets/        # Example images
│       ├── test_quickstart.py
│       └── README.md
├── README.md              # This file
├── .gitignore
└── GITHUB_SETUP.md        # GitHub setup guide
```

## 📄 Citation

If you find this repository useful for your research, please cite the original papers:

### DIFIX3D+

```bibtex
@inproceedings{wu2025difix3d+,
  title={DIFIX3D+: Improving 3D Reconstructions with Single-Step Diffusion Models},
  author={Wu, Jay Zhangjie and Zhang, Yuxuan and Turki, Haithem and Ren, Xuanchi and Gao, Jun and Shou, Mike Zheng and Fidler, Sanja and Gojcic, Zan and Ling, Huan},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  pages={26024--26035},
  year={2025}
}
```

## 🔗 Related Resources

### 3D Gaussian Splatting
- [Original 3DGS Paper](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/) - Kerbl et al., SIGGRAPH 2023
- [Awesome 3D Gaussian Splatting](https://github.com/MrNeRF/awesome-3D-gaussian-splatting)

### NeRF and Novel View Synthesis
- [NeRF: Neural Radiance Fields](https://www.matthewtancik.com/nerf)
- [Awesome NeRF](https://github.com/yenchenlin/awesome-NeRF)

## 📝 License

This repository contains implementations of research papers. Each sub-project follows its original license:

- **DIFIX3D+**: NVIDIA License (see `DIFIX3D+/Difix3D/LICENSE.txt`)

Please refer to individual project directories for specific license information.

## 🙏 Acknowledgments

We thank the authors of the original papers and their open-source contributions:
- NVIDIA Toronto AI Lab for DIFIX3D+
- The 3D Gaussian Splatting community
- Hugging Face for model hosting

## 📧 Contact

For questions or issues:
- Open an issue in this repository
- Refer to the original paper repositories for paper-specific questions

## ⚠️ Disclaimer

This repository is for research and educational purposes only. The implementations are based on publicly available papers and code. All credits go to the original authors.

---

## 中文

3D高斯溅射（3D Gaussian Splatting）研究论文实现与复现集合。

## 📚 已实现论文

### DIFIX3D+: 使用单步扩散模型改进3D重建

**作者**: Jay Zhangjie Wu*, Yuxuan Zhang*, Haithem Turki, Xuanchi Ren, Jun Gao, Mike Zheng Shou, Sanja Fidler, Zan Gojcic†, Huan Ling† (*共同第一作者, †共同指导)

**会议**: CVPR 2025 (Oral)

**论文**: [arXiv:2503.01774](https://arxiv.org/abs/2503.01774)

**项目主页**: [https://research.nvidia.com/labs/toronto-ai/difix3d/](https://research.nvidia.com/labs/toronto-ai/difix3d/)

**官方仓库**: [https://github.com/nv-tlabs/Difix3D](https://github.com/nv-tlabs/Difix3D)

**Hugging Face**: [https://huggingface.co/nvidia/difix](https://huggingface.co/nvidia/difix)

**状态**: ✅ 成功复现

**位置**: `DIFIX3D+/Difix3D/`

#### 摘要
DIFIX3D+ 提出了一种单步扩散模型，通过去除渲染视图中的伪影来改进3D重建。该方法利用扩散模型来增强3D高斯溅射重建的质量。

#### 主要特性
- 单步扩散去除伪影
- 支持参考图像引导
- 兼容多种3D重建方法
- GPU实时推理

## 🚀 快速开始

### 环境要求
- Python 3.10+
- CUDA 11.8+ (推荐用于GPU加速)
- PyTorch 2.0+
- 8GB+ GPU显存 (用于推理)

### 安装

#### DIFIX3D+

```bash
# 进入项目目录
cd DIFIX3D+/Difix3D

# 创建conda环境
conda create -n difix3d python=3.10 -y
conda activate difix3d

# 安装PyTorch和CUDA
conda install pytorch torchvision pytorch-cuda=11.8 -c pytorch -c nvidia -y

# 安装依赖
pip install -r requirements.txt
```

### 使用方法

#### 基础推理

```bash
python test_quickstart.py
```

#### 自定义图像处理

```python
from pipeline_difix import DifixPipeline
from diffusers.utils import load_image

# 加载模型
pipe = DifixPipeline.from_pretrained("nvidia/difix", trust_remote_code=True)
pipe.to("cuda")

# 处理图像
input_image = load_image("path/to/your/image.png")
output_image = pipe(
    "remove degradation",
    image=input_image,
    num_inference_steps=1,
    timesteps=[199],
    guidance_scale=0.0
).images[0]

output_image.save("output.png")
```

## 📁 项目结构

```
3dgsplus/
├── DIFIX3D+/              # DIFIX3D+ 实现
│   └── Difix3D/
│       ├── src/           # 源代码
│       ├── assets/        # 示例图像
│       ├── test_quickstart.py
│       └── README.md
├── README.md              # 本文件
└── .gitignore
```

## 📄 引用

如果您觉得本仓库对您的研究有帮助，请引用原始论文：

### DIFIX3D+

```bibtex
@inproceedings{wu2025difix3d+,
  title={DIFIX3D+: Improving 3D Reconstructions with Single-Step Diffusion Models},
  author={Wu, Jay Zhangjie and Zhang, Yuxuan and Turki, Haithem and Ren, Xuanchi and Gao, Jun and Shou, Mike Zheng and Fidler, Sanja and Gojcic, Zan and Ling, Huan},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  pages={26024--26035},
  year={2025}
}
```

## 🔗 相关资源

### 3D高斯溅射
- [原始3DGS论文](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/) - Kerbl et al., SIGGRAPH 2023
- [Awesome 3D Gaussian Splatting](https://github.com/MrNeRF/awesome-3D-gaussian-splatting)

### NeRF与新视角合成
- [NeRF: Neural Radiance Fields](https://www.matthewtancik.com/nerf)
- [Awesome NeRF](https://github.com/yenchenlin/awesome-NeRF)

## 📝 许可证

本仓库包含研究论文的实现。每个子项目遵循其原始许可证：

- **DIFIX3D+**: NVIDIA许可证 (参见 `DIFIX3D+/Difix3D/LICENSE.txt`)

具体许可信息请参考各项目目录。

## 🙏 致谢

感谢原始论文作者及其开源贡献：
- NVIDIA Toronto AI Lab 的 DIFIX3D+
- 3D高斯溅射社区
- Hugging Face 模型托管

## 📧 联系方式

如有问题或建议：
- 在本仓库提交issue
- 论文相关问题请参考原始论文仓库

## ⚠️ 免责声明

本仓库仅用于研究和教育目的。实现基于公开发表的论文和代码。所有功劳归于原作者。
