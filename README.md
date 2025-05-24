# Three-Stage Yolov8 Framework for ID-Card Forgery Detection Based on Copy-Paste Induced Boundary Artefacts


This is a novel three-stage computer vision framework as a sustainable engineering solution that integrates YOLOv8, a powerful deep learning model for object detection, with the Error Level Analysis (ELA) technique to authenticate scanned images of ID cards.
<br/>
<br/>

<div class="images" display="flex" justify-content="space-evenly">
  <img src="https://github.com/projjal2025/yolov8-ID-card/blob/main/assets/2.png" width="48%" display="inline-block" alt="sample"/>
  <img src="https://github.com/projjal2025/yolov8-ID-card/blob/main/assets/16.png" width="48%" display="inline-block" alt="sample"/>
  <p>** These images are samples of outcome of this framework. The sensitive informations are hidden for security reasons **</p>
</div>

## CONTENT

1. [Introduction](https://github.com/projjal2025/yolov8-ID-card/blob/main/README.md#introduction)
2. 


## Introduction:
This repository introduces a three-stage computer vision framework designed to validate ID cards by detecting Copy Paste Tampering Boundary Artefacts (CPTBA) signatures. These signatures are tell-tale signs of copy-paste forgery in crucial ID card fields. The framework operates as follows:

### 1. Error Level Analysis (ELA) Module:
   The initial stage employs an ELA module to analyze the ID card image for varying Discrete Cosine Transform (DCT) compression levels. Fake ID cards, often created by copying and pasting elements from different sources, exhibit these varying compression levels in tampered regions. The ELA module outputs an ELA image where CPTBA signatures and background inconsistencies are highlighted.
### 2. YOLOv8-based CPTBA Detection:
   The second stage utilizes a YOLOv8 deep learning model to detect the highlighted CPTBA signatures within the ELA image.
### 3. Tampering Field Localization:
   The final stage leverages the CPTBA detection results from YOLOv8 to generate a refined bounding box, precisely localizing the tampered field in the original ID card image.
This framework was developed and extensively tested using a custom dataset due to the absence of publicly available standard ID card image datasets. Our experiments demonstrate its viability and improved performance compared to standalone Error Level Analysis (ELA), a common copy-paste forgery detection technique.

## Features:
1. Takes very less time to test large amount of identity documents in image format.
2. Fully functional on Google Colab with the help of Google drive.
3. Higher accuracy (95%) from trained on very small dataset.
4. Saving/Resuming training after any epoch.
5. It can be worked on any type of documents(like: Id card, Invoice, legal documents, raw image).

## Flow-diagram:
<img src="https://github.com/projjal2025/yolov8-ID-card/blob/main/assets/propsed_framework.png" alt="flow-diagram"/>

