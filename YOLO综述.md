<center><span style = "font-size:3rem; font-weight:bold;">YOLO目标检测算法原理及应用</span></center>

| 版本   | 作者     | 时间      | 备注           |
| ------ | -------- | --------- | -------------- |
| V1.0.0 | Zhe Chen | 2021.1.22 | YOLO与RCNN之争 |

<div style = "page-break-after: always;"></div>

[toc]



<div style = "page-break-after: always;"></div>



# Preface

## What's the Object detection?

![image-20210122161019133](/home/pc/.config/Typora/typora-user-images/image-20210122161019133.png)

**目标检测 **的任务是找出图像中所有感兴趣的目标（物体），确定它们的位置和大小，是机器视觉领域的核心问题之一。由于各类物体有不同的外观，形状，姿态，加上成像时光照，遮挡等因素的干扰，目标检测一直是机器视觉领域最具有挑战性的问题。

计算机视觉中关于图像识别有四大类任务：

* **分类-Classification**：解决“是什么？”的问题，即给定一张图片或一段视频判断里面包含什么类别的目标。
* **定位-Location**：解决“在哪里？”的问题，即定位出这个目标的的位置。
* **检测-Detection**：解决“是什么？在哪里？”的问题，即定位出这个目标的的位置并且知道目标物是什么。
* **分割-Segmentation**：分为实例的分割（Instance-level）和场景分割（Scene-level），解决“每一个像素属于哪个目标物或场景”的问题。

## What's the core problem in Object detection

除了图像分类之外，目标检测要解决的核心问题是：

1. 目标可能出现在图像的任何位置。 

2. 目标有各种不同的大小。

3. 目标可能有各种不同的形状。

   > 如果用矩形框来定义目标，则矩形有不同的宽高比。由于目标的宽高比不同，因此采用经典的滑动窗口+图像缩放的方案解决通用目标检测问题的成本太高。

## Basical knowledge



## YOLO V.S R-CNN

目标检测架构分为两种，一种是two-stage(R-CNN)，一种是one-stage(YOLO)，区别就在于 two-stage 有候选框提取（region proposal） 过程，类似于一种海选过程，网络会根据候选区域生成位置和类别，而 one-stage 直接从图片生成位置和类别。

相对于R-CNN系列的"看两眼"(候选框提取与分类)，YOLO只需要Look Once。YOLO统一为一个回归问题，而R-CNN将检测结果分为两部分求解：物体类别（分类问题），物体位置即bounding box（回归问题）。

### YOLO（YOU ONLY LOOK ONCE）

![image-20210122165719508](/home/pc/.config/Typora/typora-user-images/image-20210122165719508.png)

YOLO的核心思想就是利用整张图作为网络的输入，直接在输出层回归bounding box的位置和bounding box所属的类别。

### R-CNN

2014年CVPR上的经典paper：《Rich feature hierarchies for Accurate Object  Detection and Segmentation》，这篇文章的算法思想又被称之为：R-CNN（Regions with  Convolutional Neural Network Features），是物体检测领域曾经获得state-of-art精度的经典文献。

这篇paper的思想，改变了物体检测的总思路，现在好多文献关于深度学习的物体检测的算法，基本上都是继承了这个思想，比如：《Spatial  Pyramid Pooling in Deep Convolutional Networks for Visual  Recognition》，所以学习经典算法，有助于我们以后搞物体检测的其它paper。

>之前刚开始接触物体检测算法的时候，老是分不清deep learning中，物体检测和图片分类算法上的区别，弄得我头好晕，终于在这篇paper上，看到了解释。
>
>> **物体检测和图片分类的区别：图片分类不需要定位，而物体检测需要定位出物体的位置，也就是相当于把物体的bbox检测出来，还有一点，物体检测是要把所有图片中的物体都识别定位出来。**







# YOLO

## YOLOv1

## How to make it

* 将一幅图像分成SxS个网格(grid cell)，如果某个object的中心 落在这个网格中，则这个网格就负责预测这个object。

  ![image-20210122173355518](/home/pc/.config/Typora/typora-user-images/image-20210122173355518.png)

* 每个网络需要预测B个BBox的位置信息和confidence（置信度）信息，一个BBox对应着四个位置信息和一个confidence信息。confidence代表了所预测的box中含有object的置信度和这个box预测的有多准两重信息：

* 325

* 325

* 435

* 













































































































