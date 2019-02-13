# Computer Vision cheatsheet
## resources
* course
  * [cs229](https://www.coursera.org/learn/machine-learning)
  * [cs231n](http://cs231n.github.io)
  * [台大李宏毅系列课程](https://www.youtube.com/channel/UC2ggjtuuWvxrHHHiaDH1dlQ)
* pytorch
  * [pytorch examples](https://github.com/pytorch/examples/)
  * [pytorch tutorial](https://pytorch.org/tutorials/)
## views
* [Convolutional Neural Networks](https://www.zhihu.com/question/39022858/answer/194996805)

## Convolutional Neural Networks
### Convolutional Networks that have a name
转自[这里](http://cs231n.github.io/convolutional-networks/)
item     | year|   author|remark|
-------- | -----|---|--
LeNet  | 1990|Yann LeCun|第一个卷积网络的应用，其中最有名的是[LeNet](http://yann.lecun.com/exdb/publis/pdf/lecun-98.pdf)识别数字和邮政编码的结构|
[AlexNet](http://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks)  | 2012|Alex Krizhevsky, Ilya Sutskever 和 Geoff Hinton|第一个使卷积神经网络在计算机视觉界流行的架构，AlexNet在2012年的[ImageNet ILSVRC challenge](http://www.image-net.org/challenges/LSVRC/2014/)中性能远超第二名（16%的top5错误率，第二名是26%的top5错误率）。这个网络架构与LeNet很相似，但更深更大，多个卷积层叠在一起（之前通常是卷积层之后立即跟上一个池化层）
[ZF NET](http://arxiv.org/abs/1311.2901)|2013|Matthew Zeiler.Rob Fergus|ILSVRC 2013年的赢家，它在AlexNet的基础上调整了一些超参数，尤其是扩大了中间卷积层的尺寸，让第一层的stride和滤波器尺寸更小
[GoogLeNet](https://arxiv.org/abs/1409.4842)|2014|Szegedy et al from Google|它主要的贡献就是提出了Inception Module，大大减少了网络中的超参数（4M，而AlexNet中有60M）。此外，这儿么论文使用了平均池化而不是在最后使用全连接层，减少了很多不必要的参数。GoogLeNet也有很多后续版本，最近的是[Inception-v4](https://arxiv.org/abs/1602.07261)
[VGGNet](http://www.robots.ox.ac.uk/~vgg/research/very_deep/)|2014|Karen Simonyan and Andrew Zisserman|ILSVRC 2014的亚军，它主要的贡献是展示了深度不是好的表现的必要元素，它们最终的网络包括16层CONV/FC层，而且网络结构极其一致，仅仅使用了3×3的卷积和2×2的池化层。它们的预训练模型在Caffe中包含了。VGGNet的一个缺点是消耗了更多的内存和参数（140M）。大多数的参数是在全连接层中，也就是那时人们发现这些全连接层可以在不降低表现的情况下被移除，大大减少了必要参数的个数
|[ResNet](https://arxiv.org/abs/1512.03385)|2015|Kaiming He et al|ILSVRC2015的赢家，它使用了特殊的跳跃连接及大量的[batch normalization](https://arxiv.org/abs/1502.03167)。这个结构在最后也没有使用全连接层。读者可以看看Kaiming的演讲（[video](https://www.youtube.com/watch?v=1PGLj-uKT1w),[slides](http://research.microsoft.com/en-us/um/people/kahe/ilsvrc15/ilsvrc2015_deep_residual_learning_kaiminghe.pdf)），以及最近一些Torch的复现[实验](https://github.com/gcr/torch-residual-networks)。ResNet是目前最先进的卷积神经网络模型，且是目前应用卷积网络的默认选择（2016年5月10日）。Kaiming He等人最近的对网络的调整[在这](https://arxiv.org/abs/1603.05027)，于2016年3月发表