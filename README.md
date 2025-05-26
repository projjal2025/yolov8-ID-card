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
   - [Error Level Analysis (ELA) Module](https://github.com/projjal2025/yolov8-ID-card/blob/main/README.md#1-error-level-analysis-ela-module)
   - [YOLOv8-based CPTBA Detection](https://github.com/projjal2025/yolov8-ID-card/blob/main/README.md#2-yolov8-based-cptba-detection)
   - [Tampering Field Localization](https://github.com/projjal2025/yolov8-ID-card/blob/main/README.md#3-tampering-field-localization)
2. [Features](https://github.com/projjal2025/yolov8-ID-card/blob/main/README.md#-features)
3. [Flow-diagram](https://github.com/projjal2025/yolov8-ID-card/blob/main/README.md#-flow-diagram)
4. [Train and Test on your custom dataset](https://github.com/projjal2025/yolov8-ID-card/tree/main?tab=readme-ov-file#-train-and-test-on-your-custom-dataset)
   - [Dataset preparation](https://github.com/projjal2025/yolov8-ID-card/tree/main?tab=readme-ov-file#1-dataset-preparation)
   - [Labelling the dataset](https://github.com/projjal2025/yolov8-ID-card/tree/main?tab=readme-ov-file#2-labelling-the-dataset)
   - [Google drive folder arrangement](https://github.com/projjal2025/yolov8-ID-card/tree/main?tab=readme-ov-file#3-google-drive-folder-arrangement)


## ✨ Introduction:
This repository introduces a three-stage computer vision framework designed to validate ID cards by detecting Copy Paste Tampering Boundary Artefacts (CPTBA) signatures. These signatures are tell-tale signs of copy-paste forgery in crucial ID card fields. The framework operates as follows:

### <ins>1. Error Level Analysis (ELA) Module:</ins>
   The initial stage employs an ELA module to analyze the ID card image for varying Discrete Cosine Transform (DCT) compression levels. Fake ID cards, often created by copying and pasting elements from different sources, exhibit these varying compression levels in tampered regions. The ELA module outputs an ELA image where CPTBA signatures and background inconsistencies are highlighted.
### <ins>2. YOLOv8-based CPTBA Detection:</ins>
   The second stage utilizes a YOLOv8 deep learning model to detect the highlighted CPTBA signatures within the ELA image.
### <ins>3. Tampering Field Localization:</ins>
   The final stage leverages the CPTBA detection results from YOLOv8 to generate a refined bounding box, precisely localizing the tampered field in the original ID card image.
This framework was developed and extensively tested using a custom dataset due to the absence of publicly available standard ID card image datasets. Our experiments demonstrate its viability and improved performance compared to standalone Error Level Analysis (ELA), a common copy-paste forgery detection technique.

## ✨ Features:
1. Takes very less time to test large amount of identity documents in image format.
2. Fully functional on Google Colab with the help of Google drive.
3. Higher accuracy (95%) from trained on very small dataset.
4. Saving/Resuming training after any epoch.
5. It can be worked on any type of documents(like: Id card, Invoice, legal documents, raw image).
6. Work with your custom dataset.

## ✨ Flow-diagram:
<img src="https://github.com/projjal2025/yolov8-ID-card/blob/main/assets/propsed_framework.png" alt="flow-diagram"/>
<p>** This is a simple flow-diagram of the framework. **</p>

## ✨ Train and Test on your custom dataset:
### 1. <ins>Dataset preparation:</ins>
Due to non-availability of a standard ID-card dataset, I created a dataset with the help of 130 students of my college. From 130 images, I created 105 forgery images consisted of **changed ID-photo, changed person name and changed person signature**.<br/>Now, 5 images are for testing and remaining 100 forgery images I divided them in **4 : 1** ratio for train and validation while training the Yolov8 model.<br/>For producing the forgery ID-card images I used [photopea.com](https://www.photopea.com/), it is a free alternative of Adobe photoshop, a web based application where you will get all greate features of Photoshop (Not promoting, it's truely amazing...👌)

### 2. <ins/>Labelling the dataset:</ins>
As here I used the Yolov8 model for object detection so, here the bounding box annotation was needed. For annotation I used LabelImg tool, you can go to it's github repository [get here](https://github.com/HumanSignal/labelImg) and install accordingly. After that, keep the labelling data of train and validation images in the 'label' folder inside of 'train' and 'val' folder in your project root directory which will be later uploaded on Google drive. Also, before opening make sure a classes.txt file is ready which will be contained the class name whichever objects you want to be detected by Yolov8.<br/>
You can see the demo video [here](https://youtu.be/p0nR2YsCY_U?si=LLlsL14_8teorXTu).

### 3. <ins>Google drive folder arrangement:</ins>
I had done the whole project on Google colab with using Google drive. So, I gave the full folder arrangement in the 'googleDrive' folder in this repository you can refer to them.<br/>
I also gave a map for folder arrangement below:
<pre>
  <code>
    <strong>Project_Root</strong>
    ├── <strong>train</strong>
    │   ├── <strong>images</strong> --> keep your images for training
    │   ├── <strong>labels</strong> --> keep your labels of images for training
    ├── <strong>val</strong>
    │   ├── <strong>images</strong> --> keep your images for validation
    │   ├── <strong>labels</strong> --> keep your labels of images for validation
    ├── <strong>test</strong>
    |   ├── <strong>real_image</strong> --> keep your images for testing
    │   ├── <strong>ELA_image</strong> --> the testing program 'ID_card_testing.ipynb' will store the ELA images after converting
    │   ├── <strong>predicted_image</strong> --> here the colored images will be stored after localization on the boundary artefacts 
    ├── <strong>runs</strong> --> yolov8 model will store the ELA images with predictions
    ├── <strong>classes.txt</strong> --> here all class names will be written for 'LabelImg' to annotate
    ├── <strong>data_custom.yaml</strong> --> here paths of 'train' and 'val' folders, number of classes and class names will be written to train the Yolov8 model.
    ├── <strong>yolov8x.pt</strong> --> pre-trained model
    ├── <strong>ELA_Converter.ipynb</strong> --> program for converting real forgery images into ELA images for training
    ├── <strong>ID_card_testing.ipynb</strong> --> program for testing ELA module, Yolov8 detection module and localization module are included in this program
    ├── <strong>ID_card_training.ipynb</strong> --> program for training
    └── <strong>weights.pt</strong> --> no need create this file, it will be created by Yolov8 after training
  </code>
</pre>

