# Trained AuxResNet Torch models #
The depth of convolutional neural networks (CNNs) is of critical importance. There are some issues associated with the increased depth. Besides the vanishing gradient problem, very deep networks also suffer from a vanishing supervision signal problem. In the course of the investigation we presented a novel model, called **AuxResNet**, which addresses the vanishing supervision signal problem through the use of additional auxiliary outputs. We proposed a *multi-way gradient backpropagation* method to train the models. As a result, the proposed **AuxResNet** gives rise to a more compact network and achieves state-of-the-art performance on various data sets. **AuxResNet** also helps to produce multiple models of different depths, thus offering the opportunity for a form of model selection.

This repository contains the trained models of **AuxResNet** using the multi-way backpropagation. These models are trained on CIFAR and SVHN. The performances of AuxResNet on these benchmark data sets are included below.

Testing error on CIFAR

| network       | outputs position | CIFAR10 | CIFAR100  |
| ------------- |:-------------:|:-------------:|:-----:|
| ResNet-1001| {1001} | 4.62 | 22.71 |
| AuxResNet-56-2| {56, 45} | 5.89 | 26.83 |
| AuxResNet-56-5| {56, 45, 35, 25, 15} | 5.53      | 26.62 |
| AuxResNet-26-2/10| {26, 19} | **3.77** | **19.69** |

Testing error on SVHN

| network        | outputs position | SVHN  |
| ------------- |:-------------:|:-----:|
| ResNet-56      | {56} | 2.06 |
| ResNet-56<img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger" style="border:none;"> | {56} | 1.70 |
| AuxResNet-56-2      | {56, 45} | 1.84 |
| AuxResNet-56-2<img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger" style="border:none;"> | {56, 45} | 1.63 |
| AuxResNet-56-3<img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger" style="border:none;"> | {56, 45, 35} | **1.58** |

<img src="http://i.imgur.com/KLThhLO.jpg" width = "420" height = "350" alt="图片名称" align=center />
<img src="http://i.imgur.com/jFMEh0c.jpg" width = "420" height = "350" alt="图片名称" align=center />

## Trained Models ##
- [CIFAR10-AuxResNet-56-2](https://yadi.sk/d/zMvzifB0vcyGA "AuxResNet-56-2")
- [CIFAR10-AuxResNet-56-5](https://yadi.sk/d/scmQFHGOvcyHP "AuxResNet-56-5")
- [CIFAR10-AuxResNet-26-2/10](https://yadi.sk/d/g-fKiJdKvcyJH "AuxResNet-26-2/10")
- [CIFAR100-AuxResNet-56-2](https://yadi.sk/d/9GTk0HrYvcyK6 "AuxResNet-56-2")
- [CIFAR100-AuxResNet-56-5](https://yadi.sk/d/NqIb0RYyvcyKo "AuxResNet-56-5")
- [CIFAR100-AuxResNet-26-2/10](https://yadi.sk/d/W8S5Cp3hvcyLT "AuxResNet-26-2/10")
- [SVHN-AuxResNet-56-3 <img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger">](https://yadi.sk/d/fs1xwcIzvcyBo "AuxResNet-56-3")

## Model Testing ##
All images don't need to be pre-processed and you just need to prepare these data sets as below. For convenience, we also provide the original data sets in torch format.

- [CIFAR-10](https://yadi.sk/d/HvwH2jJBvcyTV "cifar10") ([data preparation script](https://github.com/guoyongcn/auxresnet/blob/master/datasets/cifar10-gen.lua "cifar10-preparation"))
- [CIFAR-100](https://yadi.sk/d/u7IJW2SEvcyUg "cifar100") ([data preparation script](https://github.com/guoyongcn/auxresnet/blob/master/datasets/cifar100-gen.lua "cifar100-preparation"))
- [SVHN](https://yadi.sk/d/BwgQII_LvfPH4 "svhn") ([data preparation script](https://github.com/guoyongcn/auxresnet/blob/master/datasets/svhn-gen.lua "svhn-preparation"))

To get the result of the AuxResNet model for given benchmark data sets, you have to download the corresponding models and move them into the directory ``` ./pretrained ```.
Then you can run the script [test.lua](https://github.com/guoyongcn/auxresnet/blob/master/test.lua "testing"). For example:

```
th test.lua -dataset CIFAR10 -trainedModel cifar10-auxresnet-26-2-wide-10 
```

## Intermediate Models ##
During the training, **AuxResNet** simultaneously generates multiple models with different depth. Take [CIFAR10-AuxResNet-56-5](https://yadi.sk/d/scmQFHGOvcyHP "AuxResNet-56-5") ([outputs file](https://yadi.sk/d/ADDekHsJvcyNk "outputs-56-5")) for example:

| intermediate models | #layers | #params |
| ------------- |:-------------:|:-----:|
|output-56| 56 | 0.85M |
|output-45| 45 | 0.48M |
|output-35| 35 | 0.18M |
|output-25| 25 | 0.09M |
|output-15| 15 | 0.03M |

To run the testing for intermediate models, simply run the script [intermediate.lua](https://github.com/guoyongcn/auxresnet/blob/master/intermediate.lua "intermediate").

```
th intermediate.lua -dataset CIFAR10 -trainedModel cifar10-auxresnet-56-5 -outputs outputs-56-5
```

## Other Models ##
Additional models in torch:

- VGG & NIN [https://github.com/szagoruyko/cifar.torch](https://github.com/szagoruyko/cifar.torch)
- Deep Networks with Stochastic Depth [https://github.com/yueatsprograms/Stochastic_Depth](https://github.com/yueatsprograms/Stochastic_Depth "StochResNet")
- Wide Residual Network [https://github.com/szagoruyko/wide-residual-networks](https://github.com/szagoruyko/wide-residual-networks "WideResNet")
- pre-act ResNet [https://github.com/KaimingHe/resnet-1k-layers](https://github.com/KaimingHe/resnet-1k-layers "preactResNet")
