# Trained AuxResNet Torch models #
This repository contains the trained models of AuxResNet with the multi-way backpropagation. These models are trained on CIFAR and SVHN. The performances of AuxResNet on these benchmark data sets are included below.

## Training ##
The training scripts come with several options, which can be listed the --help flag.

```
th main.lua --help
```

To run the training, simply run main.lua. By default, the script runs AuxResNet-26-2/10 on CIFAR10 with 1GPU and 2 data-loader threads.

```
th main.lua -data[CIFAR10]
```

To run AuxResNet-56-2 on 4GPUs:

```
th main.lua -depth 56 -batchsize 256 -nGPU 4 -nThreads 8 -shareGradInput true -data[CIFAR100]
```

## Intermediate Model ##
During training time, it would generate multiple models including intermedia and final model from different layer.For example:
| network       | outputs position |
| ------------- |:-------------:|
| AuxResNet-56-2| {56, 45} |
Data in this table suggests that 


## Saving Model ##
The dafault path for saving model is the root(./).

## Trained Models ##
- [CIFAR10-AuxResNet-56-2 [56, 45]](http://baidu.com "AuxResNet-56-2")
- [CIFAR10-AuxResNet-56-5 [56, 45, 35, 25, 15]](http://baidu.com "AuxResNet-56-5")
- [CIFAR10-AuxResNet-26-2/10 [26, 19]](http://baidu.com "AuxResNet-26-2/10")
- [CIFAR100-AuxResNet-56-2 [56, 45]](http://baidu.com "AuxResNet-56-2")
- [CIFAR100-AuxResNet-56-5 [56, 45, 35, 25, 15]](http://baidu.com "AuxResNet-56-5")
- [CIFAR100-AuxResNet-26-2/10 [26, 19]](http://baidu.com "AuxResNet-26-2/10")
- [SVHN-AuxResNet-56-3 [56, 45, 35]](http://baidu.com "AuxResNet-56-3")

## Testing Intermediate/Final Models ##
To get the result of a intermediate/final model for given input dataset, you can use [test.lua]() script.For example:&nbsp;&nbsp;

```
th test.lua CIFAR10 AuxResNet-26-2/10
```

Example output:&nbsp;&nbsp;

```
error 3.91
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

