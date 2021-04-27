# Face-Mask-Detector
𝐑𝐞𝐚𝐥-𝐓𝐢𝐦𝐞 𝐅𝐚𝐜𝐞 𝐦𝐚𝐬𝐤 𝐝𝐞𝐭𝐞𝐜𝐭𝐢𝐨𝐧 𝐮𝐬𝐢𝐧𝐠 𝐝𝐞𝐞𝐩𝐥𝐞𝐚𝐫𝐧𝐢𝐧𝐠


## System Overview

It detects human faces with 𝐦𝐚𝐬𝐤 𝐨𝐫 𝐧𝐨-𝐦𝐚𝐬𝐤 even in crowd in real time 

## Table of Contents
1. [Face-Mask Dataset](#Face-Mask-Dataset)
	1. [Image Sources](#1-Image-Sources)
	2. [Image Annotation](#2-Image-Annotation) 
	3. [Dataset Description](#3-Dataset-Description)
2. [Deep Learning Models](#Deep-Learning-Models)
	1. [Training](#1-Training)
	2. [Model Performance](#2-Model-Performance)
	3. [Inference](#3-Inference)
		1. [Detection on Image](#31-Detection-on-Image)
		3. [Detection on WebCam](#32-Detection-on-WebCam)
3. [Suggestions to improve Performance](#Suggestions-to-improve-Performance)
4. [References](#References)

## Face-Mask Dataset
### 1. Image Sources
- Images were collected from [Google Images](https://www.google.com/imghp?hl=en), [Bing Images](https://www.bing.com/images/trending?form=Z9LH) and some [Kaggle Datasets](https://www.kaggle.com/vtech6/medical-masks-dataset).
- Chrome Extension used to download images: [link](https://download-all-images.mobilefirst.me/)

### 2. Image Annotation
- Images were annoted using [Labelimg Tool](https://github.com/tzutalin/labelImg).

### 3. Dataset Description
- Dataset is split into 3 sets:

|_Set_|Number of images|
|:--:|:--:|
|**Training Set**| 734 |
|**Validation/Test Set**| 200 |
|**Total**|934|

## Deep Learning Models

### 1. Training

**YOLOv4 Training details**

- Data File = [obj.data](https://github.com/Bhavesh-patel585/Face_mask_detector/blob/main/yolov4_mask_detector/obj.data)
- Cfg file  = [yolov4-obj.cfg](https://github.com/Bhavesh-patel585/Face_mask_detector/blob/main/yolov4_mask_detector/yolov4-obj.cfg)
- Pretrained Weights for initialization= [yolov4.conv.137](https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.conv.137)
- Main Configs from yolov4-obj.cfg:
	- learning_rate=0.001
	- batch=64
	- subdivisions=16
	- steps=4800,5400
	- max_batches = 6000
- **YOLOv4 Training results: _0.906244 avg loss_**

**Model Performance: Metric is mAP@0.5 i.e Mean Average Precision - 84.83%**

### 3. Inference

- You can run model inference or detection on image/video/webcam.
### 3.1 Detection on Image
- **Output Image:**
	![1_output.jpg](https://github.com/adityap27/face-mask-detector/blob/master/output/1_output.jpg?raw=true) 
### 3.2 Detection on WebCam
- **Output Video:**
<p align="center">
  <img src="https://github.com/adityap27/face-mask-detector/blob/master/media/readme-webcam.gif?raw=true">
</p>

## Suggestions to improve Performance
- As described earlier that yolov4 is giving 84.53% mAP on Train Set, this can be improved by following tips if you want:

	1. Use more Training Data.
	2. Use more Data Augmentation for Training Data.
	3. Train with larger network-resolution by setting your `.cfg-file` (height=640 and width=640) (any value multiple of 32).
	4. For Detection use even larger network-resolution like 864x864.
	5. Try YOLOv5 or any other Object Detection Algorithms like SSD, Faster-RCNN, RetinaNet, etc.

## References
- [YOLOv1 Paper](https://arxiv.org/abs/1506.02640)
- [YOLOv2 Paper](https://arxiv.org/abs/1612.08242)
- [YOLOv3 Paper](https://arxiv.org/abs/1804.02767)
- [YOLOv4 Paper](https://arxiv.org/abs/2004.10934)
- [Darknet github Repo](https://github.com/AlexeyAB/darknet)
- [YOLO Inference with GPU](https://www.pyimagesearch.com/2020/02/10/opencv-dnn-with-nvidia-gpus-1549-faster-yolo-ssd-and-mask-r-cnn/)
