# PATCHES by Brody Thompson and Matthew Currie

 - All credits for the majority of the implemented code go to the authors and creators of VideoMAE
 - PATCHES is an adaptation of the VideoMAE framework, we note that much of the code parrallels that of VideoMAE. Below is the citation for credit.
 - `Zhan Tong and et al. Videomae: Masked autoencoders are data-efficient learners for self-supervised video
pre-training. In Advances in neural information processing systems 35, 2022.`
 - [Link to the Original Paper](https://arxiv.org/pdf/2203.12602)

## 🔨 Installation

# PATCHES Installation

The codebase is mainly built with following libraries:

- Python 3.6 or higher

- [PyTorch](https://pytorch.org/) and [torchvision](https://github.com/pytorch/vision). <br>
  We can successfully reproduce the main results under two settings below:<br>
  Tesla **A100** (40G): CUDA 11.1 + PyTorch 1.8.0 + torchvision 0.9.0<br>
  Tesla **V100** (32G): CUDA 10.1 + PyTorch 1.6.0 + torchvision 0.7.0

- [timm==0.4.8/0.4.12](https://github.com/rwightman/pytorch-image-models)

- [deepspeed==0.5.8](https://github.com/microsoft/DeepSpeed)

  `DS_BUILD_OPS=1 pip install deepspeed`

- [TensorboardX](https://github.com/lanpa/tensorboardX)

- [decord](https://github.com/dmlc/decord)

- [einops](https://github.com/arogozhnikov/einops)

### Note:
- We recommend you to use **`PyTorch >= 1.8.0`**.
- We observed accidental interrupt in the last epoch when conducted the pre-training experiments on V100 GPUs (PyTorch 1.6.0). This interrupt is caused by the scheduler of learning rate. We naively set  `--epochs 801` to walk away from issue :)


## ➡️ Data Preparation

Please follow the instructions in [DATASET.md](DATASET.md) for data preparation.

## 🔄 Pre-training

The pre-training instruction is in [PRETRAIN.md](PRETRAIN.md).

## ⤴️ Fine-tuning with pre-trained models

The fine-tuning instruction is in [FINETUNE.md](FINETUNE.md).

## ☎️ Contact 

Brody Thompson: brody.p.thompson.24@dartmouth.edu
Matthew Currie: Matthew.D.Currie.24@dartmouth.edu

## 👍 Acknowledgements

Once again, we give credit to the original authors of VideoMAE, we used their model as our backbone to train PATCHES
 - `Zhan Tong and et al. Videomae: Masked autoencoders are data-efficient learners for self-supervised video
pre-training. In Advances in neural information processing systems 35, 2022.`
 - [Link to the Original Paper](https://arxiv.org/pdf/2203.12602)
