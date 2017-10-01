# pytorch-gconv-experiments
Experiments with [Group Equivariant Convolutional Networks (T. S. Cohen, M. Welling, 2016)](https://arxiv.org/abs/1602.07576)  implemented in PyTorch.

# Installation

Install [GrouPy](https://github.com/adambielski/GrouPy) with PyTorch support.

# MNIST

Modified [MNIST PyTorch example](https://github.com/pytorch/examples/tree/master/mnist) validating my implementation of G-convolutions in PyTorch.

```
cd mnist
python mnist.py
```

This simple example uses p4 group convolutions and plane group spatial max pooling.

# CIFAR-10

Experiments with ResNet implementation based by [kuangliu repository](https://github.com/kuangliu/pytorch-cifar) for CIFAR-10 with PyTorch. Training uses online data augmentation with translation and flips

All planar convolutions were replaced with p4m group convolutions. The number of filters in each convolutional layer was reduced by sqrt(8) to keep similar number of parameters (following [Group Equivariant Convolutional Networks](https://arxiv.org/abs/1602.07576), section 8.2).

To train the ResNet18 network run

```
cd cifar10
python train.py --n_epochs 120 --checkpoint resnet18_p4m --lr=0.01
```

The learning rate is reduced by a factor of 0.1 after 50 and 100 epochs.

After 120 epochs, the network achieves **94.22%** on test set, compared to 93.02% using planar convolutions reported [here](https://github.com/kuangliu/pytorch-cifar).