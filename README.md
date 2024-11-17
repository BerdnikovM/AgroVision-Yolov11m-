The model was trained under these parameters:
    data="data.yaml",  # Path to the configuration data file
    epochs=50,         # Number of epochs
    imgsz=640,         # Image size
    batch=16,          # Batch size
    device=0           # Specifies the GPU (0 is the first GPU, or "cpu" for processor)

The finished model is stored along the path: AgroVision-Yolov11m-\runs\detect\train2\weights\best.pt

data.yaml is the configuration file for training the model

AgroVisionNet.ipynb - notepad where code was run to divide the dataset into three parts (train, val, test); for model training, validation and testing.

The dataset catalog contains the data on which the neural network was trained. agri_data contains the original, unsorted images and annotations.
Images catalog contains data about images for training, validation and testing.
The labels catalog contains data on annotations for training, validation and testing.

In the catalog: AgroVision-Yolov11m-\runs\detect\train2 Graphs on the results of model training are presented. The following is a description of the graphs:

1. Confusion Matrix - This is an absolute error matrix where the numbers in the cells represent the number of images/objects categorized by the model into a certain class.

Axes:
Vertical (True) - True classes of objects.
Horizontal (Predicted) - classes predicted by the model.

Each cell shows the number of objects that belong to a certain class (true class) and were classified by the model into a specific class (predicted class).
The main diagonal (top left to bottom right) represents the correct predictions of the model.
The remaining cells show the classification errors.
For example, in the first row: crop (true class):
141: correctly classified as crop.
3: incorrectly classified as weed.
87: incorrectly classified as background.

2. Confusion Matrix Normalized - It is a normalized error matrix where the numbers in the cells are expressed as fractions (from 0 to 1). It shows the probability distribution for each class.
Normalization allows you to compare classes with each other, even if they have different numbers of objects.

crop: 92% (0.92) correctly classified as crop.
weed: 91% (0.91) correctly classified as weed.

3. F1-Confidence Curve - F1-score is a harmonic average between Precision and Recall (completeness)
It is an integral metric that takes into account both the accuracy and completeness of the model. A high F1-score means that the model strikes a good balance between minimizing false positives and missing objects.

4. Precision-Confidence Curve - Precision determines the proportion of correctly classified objects among all objects predicted by the model

5. Precision-Recall Curve - This graph shows the relationship between Precision and Recall at different confidence values.

6. Recall-Confidence Curve - This graph shows how Recall (completeness) changes as the Confidence of the model changes.

7. labels - 
a) Histogram of the number of objects by class (upper left corner)
b) Grid of bounding boxes (upper right corner)
c) Distribution of the center of the bounding boxes (bottom left corner)
d) Distribution of width and height of bounding boxes (bottom right corner)

8. labels_correlogram - This graph shows the relationship between the different parameters of the bounding boxes (x, y coordinates, width width width and height height height).

9. Results - This graph provides an overview of the training results of the YOLO model, where each of the sub-graphs represents the dynamics of different metrics over the course of training

The AgroVision-Yolov11m-\runs\detect\validation catalog contains the results of running the model on validation data
The AgroVision-Yolov11m-\runs\detect\predict catalog contains the results of model runs on test data (prediction).
