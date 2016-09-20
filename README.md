#Trained AuxResNet Torch models
These are AuxResNet models trained on CIFAR and SVHN. Below is the accuracy of AuxResNet on these benchmark data sets.

## Trained Models ##
- [CIFAR10-AuxResNet-56-2 [56, 45]](http://baidu.com "AuxResNet-56-2")
- [CIFAR10-AuxResNet-56-5 [56, 45, 35, 25, 15]](http://baidu.com "AuxResNet-56-5")
- [CIFAR10-AuxResNet-26-2/10 [26, 19]](http://baidu.com "AuxResNet-26-2/10")
- [CIFAR100-AuxResNet-56-2 [56, 45]](http://baidu.com "AuxResNet-56-2")
- [CIFAR100-AuxResNet-56-5 [56, 45, 35, 25, 15]](http://baidu.com "AuxResNet-56-5")
- [CIFAR100-AuxResNet-26-2/10 [26, 19]](http://baidu.com "AuxResNet-26-2/10")
- [SVHN-AuxResNet-56-3 [56, 45, 35]](http://baidu.com "AuxResNet-56-3")

Testing error on CIFAR

| network       | outputs position | CIFAR10 | CIFAR100  |
| ------------- |:-------------:|:-------------:|:-----:|
| AuxResNet-56-2| {56, 45} | 5.89 | 26.83 |
| AuxResNet-56-5| {56, 45, 35, 25, 15} | 5.53      | 26.62 |
| AuxResNet-26-2/10| {26, 19} | 3.91      | 19.69 |

Testing error on SVHN

| network        | outputs position | SVHN  |
| ------------- |:-------------:|:-----:|
| AuxResNet-44-2      | {44, 39} | 1.96 |
| AuxResNet-56-2      | {56, 45} | 1.84 |
| AuxResNet-44-2<img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger" style="border:none;">      | {44, 39} | 1.75 |
| AuxResNet-56-2<img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger" style="border:none;"> | {56, 45} | 1.63 |
| AuxResNet-56-3<img src="http://chart.googleapis.com/chart?cht=tx&chl=^\dagger" style="border:none;"> | {56, 45, 35} | 1.58 |

