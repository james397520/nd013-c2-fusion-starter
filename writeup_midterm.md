# Sensor Fusion - 3D-Objects

In this section, I learned how to process lidar point-clouds data from waymo dataset and detect 3D object in lidar by Complex YOLO algorithm.

## Step 1. Converting Range Images to Point Clouds

### 1. Visualizing Range Images

First, the range range images can be visualiized for understanding the dataset.

![](img/midterm/range_image.png)

### 2. Converting Range Images to Point Clouds

- The point cloud data can be visualized in Open3D
- Visualize lidar point-cloud

![](img/midterm/point_cloud_1.png)

![](img/midterm/point_cloud_2.png)

![](img/midterm/point_cloud_3.png)

![](img/midterm/point_cloud_4.png)

![](img/midterm/point_cloud_5.png)

![](img/midterm/point_cloud_6.png)

![](img/midterm/point_cloud_7.png)

![](img/midterm/point_cloud_8.png)

![](img/midterm/point_cloud_9.png)

![](img/midterm/point_cloud_10.png)


The structure, edge and contour of the object from lidar point cloud data are the main features(rear-bumper, front-bumper, sides of vehicles) for the object detection algorithm. 

## Step 2. Create Birds-Eye View (BEV) from Lidar PCL

### 1. Convert sensor coordinate to BEV-map coordinates

![](img/midterm/bev_map.png)


### 2. Compute intensity/hight/density layer of the BEV map

There are three kinds of information can be oberserved for each BEV cell, wihic is `intensity`, `height`, and `density` information.

![](img/midterm/intensity_layer.png)

![](img/midterm/height_layer.png)

## Step 3. Model-based Object Detection in BEV Image

The BEV-map will be the input data for the model, and the output result is 3d bounding boxes information.

![](img/midterm/labels_detected_objects.png)


## Step 4. Performance Evaluation for Object Detection

### 1. Compute intersection-over-union (IOU) between labels and detections

### 2. Compute false-negatives and false-positives

### 4. Compote percision and recall

The precision-recall curve is plotted showing similar results of `precision = 0.9506` and `recall = 0.944`.

![](img/midterm/metric_01.png)

![](img/midterm/metric_00.png)

In the next step,  we set:

```python
configs_det.use_labels_as_objects=True
```
The resulting performance measures for this setting should be the following:

which results in `precision = 1.0 and recall = 1.0`, which is shown in the following image:

![](img/midterm/metric_11.png)

![](img/midterm/metric_10.png)
