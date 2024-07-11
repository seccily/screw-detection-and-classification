# Screw Detection and Classification

The main purpose of this project is to observe the performance of different approaches in object detection and classification problems.

## Dataset
The [screw_detection_iphone](https://universe.roboflow.com/corrosion-a1pkl/screw_detection_iphone) dataset from Roboflow was used in the project. 

There are 6 classes in the dataset:
1. Flat Head Screw
2. Hex Washer Screw
3. Hexagonal Bolt
4. Philips Screw
5. Pozidriv Screw
6. Torx Screw

No train-test splitting was made in the data set and all 1360 images were given in the train data set.

## Approach

The solution of the problem was carried out in two stages. Therefore, a preprocessing process was applied for each stage before using the data. The preprocessed version of the dataset can be found in the `dataset` folder.

### Step 1 - Detection

For this stage, the screw types given as 5 separate classes in the data set were combined to form a single class. In this way, only 2 classes, bolt and screw, were used in the detection stage.

In this way, the model only focused on detecting screws and bolts and did not try to solve the problem of distinguishing screw types. It was aimed to increase the success of the detection phase by reducing the problem complexity.

YOLOv5 was preferred as the object detection model.

### Step 2 - Classification

At this stage, the problem of classifying the detected screws was tried to be solved. The data set for the problem was created by cropping the relevant object using the ground truth labels given in the original data set. At this point, the bolt class is not included in the classification phase since it is considered separately in the detection phase.

YOLOv8 was preferred as the image classification model.