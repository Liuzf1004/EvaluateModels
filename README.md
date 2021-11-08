## Report for evaluation of  pre-trained models in PytorchVideo

### 1. Abstract

​	This report conducts evaluation work for pre-trained models in frameworks such as pytorchVideo, and a total of three major classes of these models are selected for testing, using google colab for code writing work and github for version control. And limited by the performance of google colab's cloud platform (no cuda), and the failure to find suitable annotated data, the evaluation criteria are only based on time consumption. The rest of the evaluation metrics are referred to the official documentation. The following test results were finally obtained.

### 2. Introduction

#### 2.1 Settings

​	plathform: google colab

​	version control: GitHub

​	device: cpu (ram: 12.65G)

​	programming language: python (python 3)	

​	frame: pytorchvideo

​	models: Slow (r50) 、SlowFast (r50、r101)、X3D (S、M、L)

​	metric: latency (others: top1、top5 based on official documents)

#### 2.2 detail

​	The main process of this experiment refers to the tutorial file in the official github, based on which it is modified and some of the methods are wrapped to get multiple results. For the test environment are used google colab, to ensure the consistency of the operating environment, test data because there is no additional labeled data, so the documentation examples used in https://dl.fbaipublicfiles.com/pytorchvideo/projects/archery.mp4, and then according to each model Different input transformations are processed for each model. The models are imported through the torch hub. The difference between each model's corresponding transform is large, and the code encapsulated by the class is less readable, so three different scripts were written. prediction part because the time difference between top5 and top1 is not significant, so top5 was chosen as the reference standard, the test latency excludes the model import time, only prediction In addition, because the difference between the single test time on google colab is too large, at most 80% of the difference, so each model is counted as the average of ten tests.

### 3. Results

#### 3.1 official document

​	![official document](https://github.com/liu-feng116/EvaluateModels/blob/main/1.png)

#### 3.2 latency

​		![](https://github.com/liu-feng116/EvaluateModels/blob/main/2.png)
​		![](https://github.com/liu-feng116/EvaluateModels/blob/main/3.png)
​		![](https://github.com/liu-feng116/EvaluateModels/blob/main/4.png)

### 4. Inference
https://github.com/facebookresearch/pytorchvideo
https://github.com/open-mmlab/mmaction2
https://pytorch.org/hub/facebookresearch_pytorchvideo_slowfast/
https://pytorch.org/hub/facebookresearch_pytorchvideo_x3d/
https://pytorch.org/hub/facebookresearch_pytorchvideo_resnet/
https://github.com/facebookresearch/pytorchvideo/blob/main/docs/source/model_zoo.md#kinetics-400
