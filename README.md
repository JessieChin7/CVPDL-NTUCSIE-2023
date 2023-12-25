# Computer Vision Practice and Deep Learning
2023 Spring NTU CSIE

## Homework 1: Object Detection with DINO
- **Objective**: Implement object detection using the DINO framework.
- **Techniques and Implementation**:
  - Employed advanced object detection methods using the DINO (DEtection with Transformers) framework.
  - Re-trained the model on a given dataset to tailor it for specific object detection tasks.
  - Utilized a pretrained model, `checkpoint0033_4scale.pth`, fine-tuned on the COCO 2017 dataset.
  - Backbone architecture used was R50.
- **Performance Metrics**:
  - Achieved a mean Average Precision (mAP) of 0.5233.

## Homework 2: Transformer-Based Object Detection
- **Objective**: Analyzed convergence issues in DETR models and explored advanced models and techniques.
- **Key Highlights**:
  - Analyzed DETR (End-to-End Object Detection with Transformers) for convergence issues.
  - Compared DAB-DETR and DN-DETR, addressing slow convergence of DETR.
  - Explored knowledge distillation methods, both from logits and intermediate layers.
  - Discussed CLIP's training process and zero-shot classification applications.
  - Investigated challenges in Open-Vocabulary Object Detection with RegionCLIP.

## Homework 3: Object Detection and Data Augmentation
- **Objective**: Addressed data imbalance in object detection using foundation models and data augmentation techniques.
- **Key Features**:
  - Utilized BLIP2 for image captioning and GLIGEN for data augmentation.
  - Addressed data imbalance from HW1's dataset using generated prompts for image generation.
  - Applied text-to-image generation techniques to augment object detection datasets.
  - Evaluated using Fréchet Inception Distance (FID) for the quality of generated images.
  - Improved detection model performance post data augmentation.
  - Demonstrated techniques through examples of image captioning and text-to-image generation.
