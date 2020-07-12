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

<table>
<thead>
<tr>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Author</strong></td>
<td>Trần Vĩnh Toàn- Foundation 8 - VTC AI</td>
</tr>
<tr>
<td><strong>Title</strong></td>
<td>Computer Vision - EfficientNet For Fruits &amp; Vegetables Detection App</td>
</tr>
<tr>
<td><strong>Topics</strong></td>
<td>Ứng dụng trong computer vision, sử dụng thuật toán chính là CNN</td>
</tr>
<tr>
<td><strong>Descriptions</strong></td>
<td>Input sẽ là tấm hình với các loại quả khác nhau và file labels-v2.txt chứa danh sách tên của 130 loại quả tương ứng. Dữ liệu dùng để train là dataset của 130 loại quả có kích thước (100px X 100px). Train toàn bộ dữ liệu này bằng cấu trúc mạng CNN  sử dụng model EfficientNet ( Chi tiết về model : <a href="https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet">https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet</a>, Paper: <a href="https://arxiv.org/abs/1905.11946" rel="nofollow">https://arxiv.org/abs/1905.11946</a>). khi train xong sẽ trả ra output là file trọng số <code>weights</code>. Ta sẽ sử dụng trọng số <code>weights</code> đã train để predict name của các object trong hình</td>
</tr>
<tr>
<td><strong>Links</strong></td>
<td><a href="https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet">https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet</a> , <a href="https://github.com/rwightman/pytorch-image-models">https://github.com/rwightman/pytorch-image-models</a></td>
</tr>
<tr>
<td><strong>Framework</strong></td>
<td>PyTorch</td>
</tr>
<tr>
<td><strong>Pretrained Models</strong></td>
<td>sử dụng weight đã được train sẵn <a href="https://github.com/rwightman/pytorch-image-models/releases/download/v0.1-weights/efficientnet_b3_ra-a5e2fbc7.pth">https://github.com/rwightman/pytorch-image-models/releases/download/v0.1-weights/efficientnet_b3_ra-a5e2fbc7.pth</a> <a href="https://github.com/rwightman/pytorch-image-models/releases/download/v0.1-weights/efficientnet_es_ra-f111e99c.pth">https://github.com/rwightman/pytorch-image-models/releases/download/v0.1-weights/efficientnet_es_ra-f111e99c.pth</a></td>
</tr>
<tr>
<td><strong>Datasets</strong></td>
<td>Mô hình được train với bộ dữ liệu 130 loại quả tại: <a href="https://www.kaggle.com/moltean/fruits/data" rel="nofollow">https://www.kaggle.com/moltean/fruits/data</a></td>
</tr>
<tr>
<td><strong>Level of difficulty</strong></td>
<td>Normal +, có thể train lại với tập dữ liệu khác và model khác tốc độ tùy thuộc vào CPU &amp; GPU &amp; data input</td>
</tr>
</tbody>
</table>
