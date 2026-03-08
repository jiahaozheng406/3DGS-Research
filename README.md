# 3DGS Research

[![Python](https://img.shields.io/badge/Python-3.10-blue)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red)](https://pytorch.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

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
