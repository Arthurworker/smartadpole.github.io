---
layout: article
title:  "「CV」 物体分割资源汇总"
date:   2019-05-05 18:06:40 +0800
key: image-segmentation-foundation-20190505
aside:
  toc: true
category: [AI, CV, segmentation]
tags: 资源
---
<span id='head'></span>

<!--more-->  

# 1 二维
## 1.1 综述

## 1.2 理论

1. [Learning Fully Dense Neural Networks for Image Semantic Segmentation](http://cn.arxiv.org/abs/1905.08929)   
*2019-05-22* [paper](https://arxiv.org/abs/1905.08929)   

1. [Segmentation-Aware Image Denoising without Knowing True Segmentation](http://cn.arxiv.org/abs/1905.08965)   
*2019-05-22* [paper](https://arxiv.org/abs/1905.08965)   

1. [Spatial Sampling Network for Fast Scene Understanding](http://cn.arxiv.org/abs/1905.09033)   
CVPR 2019 (Autonomous Driving) *2019-05-22* [paper](https://arxiv.org/abs/1905.09033)    

1. [End-to-End Learned Random Walker for Seeded Image Segmentation](https://arxiv.org/abs/1905.09045)   
*2019-05-22* [paper](https://arxiv.org/abs/1905.09045)   

1. [WPU-Net:Boundary learning by using weighted propagation in convolution network](https://arxiv.org/abs/1905.09226)   
*2019-05-22* [paper](https://arxiv.org/abs/1905.09226)   

## 1.3 经典

## 1.4 轮廓提取
1. [Semantic Contours from Inverse Detectors](http://home.bharathh.info/pubs/pdfs/BharathICCV2011.pdf)   
ICCV 2011 *2011* [paper](http://home.bharathh.info/pubs/pdfs/BharathICCV2011.pdf)     

## 1.5 分割
### 1.5.1 CNN
1. [ACNet: Attention Based Network to Exploit Complementary Features for RGBD Semantic Segmentation](https://arxiv.org/abs/1905.10089)   
ICIP 2019 *2019-05-24* [paper](https://arxiv.org/abs/1905.10089) | [pytorch](https://github.com/anheidelonghu/ACNet)    

1. [SegSort: Segmentation by Discriminative Sorting of Segments](https://arxiv.org/abs/1910.06962)    
ICCV 2019 *2019-10-15* [paper](https://arxiv.org/abs/1910.06962) | [project](https://jyhjinghwang.github.io/projects/segsort.html) | [tensorflow](https://github.com/jyhjinghwang/SegSort)-official    
SegSort: 大津阈值的思路；跨图像训练；    


### 1.5.2 GAN

1.  [Adversarial Deep Structural Networks for Mammographic Mass Segmentation](http://cn.arxiv.org/abs/1611.05970)   
*2016-11-18* [paper](https://arxiv.org/abs/1611.05970) | [matlab](https://github.com/wentaozhu/adversarial-deep-structural-networks)-official      

1.  [Semantic Segmentation using Adversarial Networks](http://cn.arxiv.org/abs/1611.08408)  
*2016-11-25* [paper](https://arxiv.org/abs/1611.08408)     

## 1.6 [生物医疗](/ai/cv/medical/2019/05/23/foundation.html#13-分割)


## 1.7 自然
### 1.7.1 [盐体分割](/ai/cv/nature/salt_bodies/2019/10/16/foundation.html#3-分割)
### 1.7.2 [天空分割](/ai/cv/nature/sky/2019/10/16/foundation.html#4-天空分割)
### 1.7.3 [火灾区域分割](/ai/cv/nature/fire_disaster/2019/10/16/foundation.html#3-火灾区域分割)


## 1.8 [人](/ai/cv/human/human_segmentation/2019/05/14/foundation.html)

## 1.9 交通
### 1.9.1 [车辆](/ai/cv/vehicle/vehicle_segmentation/2019/10/10/foundation.html)
### 1.9.2 交通标志   

## 1.10 高光谱
`hyperspectral image`    
1. [Statistical Loss and Analysis for Deep Learning in Hyperspectral Image Classification](http://cn.arxiv.org/abs/1912.12385)  
 *2019-12-28* [paper](https://arxiv.org/abs/1912.12385)     
 针对高光谱图像分割设计了新的统计 loss；     

# 2 序列
1. [RVOS: End-to-End Recurrent Network for Video Object Segmentation](http://cn.arxiv.org/abs/1903.05612)   
CVPR 2019 (camera ready) *2019-03-13* [paper](https://arxiv.org/abs/1903.05612) | [project](https://imatge-upc.github.io/rvos/) | [pytorch](https://github.com/imatge-upc/rvos)-official   

1. [OVSNet : Towards One-Pass Real-Time Video Object Segmentation](http://cn.arxiv.org/abs/1905.10064)   
*2019-05-24* [paper](https://arxiv.org/abs/1905.10064)   

# 3 三维
## 3.1 基于点云
1. [RIU-Net: Embarrassingly simple semantic segmentation of 3D LiDAR point cloud](https://arxiv.org/abs/1905.08748)   
*2019-05-21* [paper](https://arxiv.org/abs/1905.08748)   

## 3.2 基于体素
1. [Learning to Reconstruct High-quality 3D Shapes with Cascaded Fully Convolutional Networks](http://openaccess.thecvf.com/content_ECCV_2018/papers/Yan-Pei_Cao_Learning_to_Reconstruct_ECCV_2018_paper.pdf)    
ECCV 2018 [Paper](http://openaccess.thecvf.com/content_ECCV_2018/papers/Yan-Pei_Cao_Learning_to_Reconstruct_ECCV_2018_paper.pdf)   
3D FCN  

## 3.3 深度图
1. [RFBNet: Deep Multimodal Networks with Residual Fusion Blocks for RGB-D Semantic Segmentation](http://cn.arxiv.org/abs/1907.00135)   
*2019-06-29* [paper](https://arxiv.org/abs/1907.00135)   

# 4 全景分割
1. [Fast Panoptic Segmentation Network](http://cn.arxiv.org/abs/1910.03892)    
*2019-10-09* [paper](https://arxiv.org/abs/1910.03892)    

1. [Panoptic-DeepLab](http://cn.arxiv.org/abs/1910.04751)     
*2019-10-10* [paper](https://arxiv.org/abs/1910.04751)    


-------------------  
[End](#head)
{:.warning}  


# 附录
## A 参考资料
[1]. tangzhenyu. SemanticSegmentation_DL[EB/OL]. <https://github.com/tangzhenyu/SemanticSegmentation_DL>. -/2019-05-05.   