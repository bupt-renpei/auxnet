# Trained AuxResNet Torch models #
The depth of convolutional neural networks (CNNs) is of critical importance. There are some issues associated with the increased depth. Besides the vanishing gradient problem, very deep networks also suffer from a vanishing supervision signal problem. In the course of the investigation we presented a novel model, called **AuxResNet**, which addresses the vanishing supervision signal problem through the use of additional auxiliary outputs. We proposed a *multi-way gradient backpropagation* method to train the models. As a result, the proposed **AuxResNet** gives rise to a more compact network and achieves state-of-the-art performance on various data sets. **AuxResNet** also helps to produce multiple models of different depths, thus offering the opportunity for a form of model selection.

This repository contains the trained models of **AuxResNet** with the multi-way backpropagation. These models are trained on CIFAR and SVHN. The performances of AuxResNet on these benchmark data sets are included below.

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

![cifar10best](http://i.imgur.com/SuFADMS.jpg)


## Trained Models ##
- [CIFAR10-AuxResNet-56-2 [56, 45]](http://baidu.com "AuxResNet-56-2")
- [CIFAR10-AuxResNet-56-5 [56, 45, 35, 25, 15]](http://baidu.com "AuxResNet-56-5")
- [CIFAR10-AuxResNet-26-2/10 [26, 19]](http://baidu.com "AuxResNet-26-2/10")
- [CIFAR100-AuxResNet-56-2 [56, 45]](http://baidu.com "AuxResNet-56-2")
- [CIFAR100-AuxResNet-56-5 [56, 45, 35, 25, 15]](http://baidu.com "AuxResNet-56-5")
- [CIFAR100-AuxResNet-26-2/10 [26, 19]](http://baidu.com "AuxResNet-26-2/10")
- [SVHN-AuxResNet-56-3 [56, 45, 35]](http://baidu.com "AuxResNet-56-3")

## Model Testing ##
All images don't need to be pre-processed and you just need to prepare these data sets as below. For convenience, we also provide the original data sets in torch format.

- [CIFAR-10](http://torch.ch "cifar10") ([data preparation script](https://github.com/facebook/fb.resnet.torch/blob/master/datasets/cifar10-gen.lua "cifar10-preparation"))
- [CIFAR-100](http://torch.ch "cifar100") ([data preparation script](https://github.com/facebook/fb.resnet.torch/blob/master/datasets/cifar100-gen.lua "cifar100-preparation"))
- [SVHN](http://torch.ch "svhn") ([data preparation script](https://gist.github.com/szagoruyko/27712564a3f3765c5bfd933b56a21757 "svhn-preparation"))

To get the result of the AuxResNet model for given benchmark data sets, you have to download the corresponding models and move them into the directory ``` ./pretrained ```.
Then you can run the script [test.lua](). For example:

```
th test.lua -dataset CIFAR10 -model AuxResNet-26-2/10 
```

## Intermediate Model ##
During the training, **AuxResNet** simultaneously generates multiple models with different depth. For example:



| network       | intermediate models |
| ------------- |:-------------:|
| AuxResNet-56-2| output-56 <br> ---------------------- <br> output-45 <br> ---------------------- <br> output-35 <br> ---------------------- <br> output-25 <br> ---------------------- <br> output-15 |

Data in this table means that training system has generated 2 model including intermedia from 45 layer and final one from 56 layer.



