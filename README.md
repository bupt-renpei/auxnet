# Trained AuxResNet Torch models #
This repository contains the trained models of AuxResNet with the multi-way backpropagation. These models are trained on CIFAR and SVHN. The performances of AuxResNet on these benchmark data sets are included below.

## Trained Models ##
- [CIFAR10-AuxResNet-56-2 [56, 45]](http://baidu.com "AuxResNet-56-2")
- [CIFAR10-AuxResNet-56-5 [56, 45, 35, 25, 15]](http://baidu.com "AuxResNet-56-5")
- [CIFAR10-AuxResNet-26-2/10 [26, 19]](http://baidu.com "AuxResNet-26-2/10")
- [CIFAR100-AuxResNet-56-2 [56, 45]](http://baidu.com "AuxResNet-56-2")
- [CIFAR100-AuxResNet-56-5 [56, 45, 35, 25, 15]](http://baidu.com "AuxResNet-56-5")
- [CIFAR100-AuxResNet-26-2/10 [26, 19]](http://baidu.com "AuxResNet-26-2/10")
- [SVHN-AuxResNet-56-3 [56, 45, 35]](http://baidu.com "AuxResNet-56-3")

## Testing Models ##
To get the result of a model saving in root for given input dataset, you can use [test.lua]() script.For example:&nbsp;&nbsp;

```
th test.lua -dataset CIFAR10 -model AuxResNet-56-2.t7
th test.lua -dataset CIFAR10 -model AuxResNet-56-5.t7
th test.lua -dataset CIFAR10 -model AuxResNet-26-2/10.t7
th test.lua -dataset CIFAR10 -model AuxResNet-56-2.t7
th test.lua -dataset CIFAR10 -model AuxResNet-56-5.t7
th test.lua -dataset CIFAR10 -model AuxResNet-26-2/10.t7
th test.lua -dataset CIFAR10 -model AuxResNet-56-3.t7
```

Example output:&nbsp;&nbsp;
```
AuxResNet-56-2     error     5.89
AuxResNet-56-5     error     5.53
AuxResNet-26-2/10  error     3.91
```

## Performance ##
Testing error on CIFAR

| network       | outputs position | CIFAR10 | CIFAR100  |
| ------------- |:-------------:|:-------------:|:-----:|
| ResNet-1001| {1001} | 4.62 | 22.71 |
| AuxResNet-56-2| {56, 45} | 5.89 | 26.83 |
| AuxResNet-56-5| {56, 45, 35, 25, 15} | 5.53      | 26.62 |
| AuxResNet-26-2/10| {26, 19} | **3.91** | **19.69** |

Testing error on SVHN

| network        | outputs position | SVHN  |
| ------------- |:-------------:|:-----:|
| AuxResNet-44-2      | {44, 39} | 1.96 |
| AuxResNet-56-2      | {56, 45} | 1.84 |
| AuxResNet-44-2<img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger" style="border:none;">      | {44, 39} | 1.75 |
| AuxResNet-56-2<img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger" style="border:none;"> | {56, 45} | 1.63 |
| AuxResNet-56-3<img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger" style="border:none;"> | {56, 45, 35} | **1.58** |

![cifar10best](http://i.imgur.com/dlOHhZZ.jpg)
![](http://i.imgur.com/dlOHhZZ.jpg =100*100)

## Intermediate Models ##

To get the result of a intermediate model for given imput dataset, you can use [intermedia.lua]() script. For example:&nbsp;&nbsp;
```
th intermedia.lua -dataset CIFAR10 -model AuxResNet-56-2.t7 -fc fc.t7
```

Example model:&nbsp;&nbsp;

| network       | outputs position |
| ------------- |:-------------:|
| AuxResNet-56-5| {56, 45, 35, 25, 15} |

&nbsp;&nbsp;

Example output: &nbsp;&nbsp;
```
Model   AuxResNet-56-5
layer15  error  [err_num]
layer25  error  [err_num]
layer35  error  [err_num]
layer45  error  [err_num]
layer56  error  [err_num]
```

