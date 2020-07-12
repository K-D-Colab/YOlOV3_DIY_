# keras-yolo3

[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](LICENSE)

## Introduction

A Keras implementation of YOLOv3 (Tensorflow backend) inspired by [allanzelener/YAD2K](https://github.com/allanzelener/YAD2K).


---

## Quick Start

1. Download YOLOv3 weights from [YOLO website](http://pjreddie.com/darknet/yolo/).
2. Run YOLO detection.

### Usage
Use --help to see usage of yolo_camera.py:
```
usage: yolo_camera.py 
    net = cv2.dnn.readNet('yolov3-test.weights', 'yolov3-test.cfg')
    classes_number = "model_data\test_classes.txt"

## Training

1. Generate your own annotation file and class names file.  
    One row for one image;  
    Row format: `image_file_path box1 box2 ... boxN`;  
    Box format: `x_min,y_min,x_max,y_max,class_id` (no space).  
    For VOC dataset, try `python voc_annotation.py`  
    Here is an example:
    ```
    path/to/img1.jpg 50,100,150,200,0 30,50,200,120,3
    path/to/img2.jpg 120,300,250,600,2
    ...
    ```

2. Make sure you have run `python convert.py -w yolov3.cfg yolov3.weights model_data/yolo_weights.h5`  
    The file model_data/yolo_weights.h5 is used to load pretrained weights.

3. Modify train.py and start training.  
    `python train.py`  
    Use your trained weights or checkpoint weights with command line option `--model model_file` when using yolo_video.py
    Remember to modify class path or anchor path, with `--classes class_file` and `--anchors anchor_file`.

If you want to use original pretrained weights for YOLOv3:  
    1. `wget https://pjreddie.com/media/files/darknet53.conv.74`  
    2. rename it as darknet53.weights  
    3. `python convert.py -w darknet53.cfg darknet53.weights model_data/darknet53_weights.h5`  
    4. use model_data/darknet53_weights.h5 in train.py

<div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6">
    <article class="markdown-body entry-content container-lg" itemprop="text"><table>
<thead>
<tr>
<th><strong>Title</strong></th>
<th>Home Credit Default Risk</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Team</strong></td>
<td>Nguyễn Hải Linh - <a href="mailto:hailinh.leo@gmail.com">hailinh.leo@gmail.com</a></td>
</tr>
<tr>
<td><strong>Predicting</strong></td>
<td>Predicting Default Risk of loan application, based on Home Credit dataset (it's a Kaggle Competition)</td>
</tr>
<tr>
<td><strong>Data</strong></td>
<td>I got data from Kaggle Competition, hosted by Home Credit. The dataset includes many csv files from many tables of their database, but for the purpose of making final project for ML course, plus the limitation in time and hardware, I took only 1 table for this practical essay: application.csv</td>
</tr>
<tr>
<td><strong>Features</strong></td>
<td>There are 122 features, which are raw input data. I created 4 more fields: train-error-mean, train-error-std, train-error-mean, test-error-std to measure the feature importance, then based on that reduced the dimension to only 49.</td>
</tr>
<tr>
<td><strong>Models</strong></td>
<td>I mainly use XGBoost: ∑𝑗=1𝑇[(∑𝑖∈𝐼𝑗𝑔𝑖)𝑤𝑗+12(∑𝑖∈𝐼𝑗ℎ𝑖+𝜆)𝑤2𝑗]+𝛾𝑇, which is believed to be one of the best model for controlling overfitting. I added cross-validation function: k-fold to utilise the power of XGBoost.</td>
</tr>
<tr>
<td><strong>Results</strong></td>
<td></td>
</tr>
<tr>
<td></td>
<td>XGB training set 150679.000</td>
</tr>
<tr>
<td></td>
<td>XGB test set 92254.000</td>
</tr>
<tr>
<td></td>
<td>XGB auc score 0.748</td>
</tr>
<tr>
<td></td>
<td>MLP training set 150679.000</td>
</tr>
<tr>
<td></td>
<td>MLP test set 92254.000</td>
</tr>
<tr>
<td></td>
<td>MLP auc score 0.605</td>
</tr>
<tr>
<td><strong>Discussion</strong></td>
<td>Decision tree algorithsm is the best for making scoring model. Besides the accuracy / auc metrics that could be maximised by boosted trees (in this project is XGBoost), we can also clearly see feature importance, which is more difficult to find in other modern model like MLP. In financial institution, data is money. With feature importance, we can save a lot by reducing expense on buying personal data, optimise customer experience (less fields in loan application) and save cost for computing.</td>
</tr>
<tr>
<td><strong>Future</strong></td>
<td>There are still 5 more tables that haven't been exploited this time, due to limitation of time. There other tables will require more data processing skills, which could increase the auc score a little bit (based on other's result on Kaggle).</td>
</tr>
<tr>
<td><strong>References</strong></td>
<td><a href="https://www.kaggle.com/c/home-credit-default-risk/overview/description" rel="nofollow">https://www.kaggle.com/c/home-credit-default-risk/overview/description</a></td>
</tr>
</tbody>
</table>
</article>
  </div>