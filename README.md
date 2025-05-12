# object-detection-model-for-service-robots
Object detection model for service robots in restaurants

1.Summary

The aim of this project is to develop an object detection model for service robots in restaurants, capable of accurately detecting white cups and plates supported by Time-of-Flight (ToF) sensor data. The model is designed to enhance operational efficiency by enabling robots to identify objects quickly and safely during the service process. The project comprehensively covers image data collection, preprocessing, model training, and testing procedures.

2. Data Collection and Preparation

Data Collection Scenarios:

The data were collected using a mobile phone camera with a 2MP resolution, capturing images at 1600x1200 pixels. To increase contrast for object detection (cup and plate), a black table or background was used. Recordings were performed under three different scenarios:

    Scenario 1: Only cup (5 seconds)

    Scenario 2: Only plate (5 seconds)

    Scenario 3: Cup and plate together (5 seconds)

Data Preprocessing:

Images were resized to a standardized dimension of 1600x1200 pixels. Labeling was carried out using the LabelImg tool in YOLO format (class_id, x_center, y_center, width, height); class 0 was assigned to cups and class 1 to plates. Additionally, contrast and brightness adjustments were applied to improve object visibility.

Dataset Distribution:

The dataset was split into two main parts: training 240 img and validation 60 img. 

3. Model Training

Model and Framework:

The YOLOv11s model was selected for object detection.

Training Parameters:

The model was trained using specific parameters (e.g., 100 epochs, batch size of 16, image size of 640). Transfer learning with pre-trained weights was employed to reduce training time.

Performance Metrics:

The model’s success was evaluated using the following metrics: mAP@0.8 (0.96 for cup, 0.94 for plate), precision (0.95), and recall (0.93). These metrics indicate the model achieved a high level of accuracy and reliability.

4. Test Video and Outputs

The test video was recorded at 1600x1200 pixel resolution and includes objects at three distinct time intervals:

    0–5 seconds: Only cup

    5–10 seconds: Only plate

    10–15 seconds: Cup and plate together

During testing, the model annotated detected objects in each frame with bounding boxes and saved detection information to a text file. Example detections include:

    Frame 15 (00:00:05): "cup" detected, coordinates (320,150,480,400)

    Frame 30 (00:00:10): "plate" detected, coordinates (600,200,800,450)

5. Challenges and Solutions

Corrupted Video Output:

Issues related to frame size and file compatibility occurred in the output video. These were resolved using OpenCV’s resizing functions and by selecting an appropriate codec (XVID).

Preventing False Positives:

The model occasionally detected irrelevant objects. To mitigate this, a confidence threshold of 80% was set. Only detections with a confidence score of 80% or higher were processed, excluding undesired or foreign objects.

6. Conclusion and Recommendations

Conclusion:

The model successfully detected cup and plate objects in the test video with an accuracy rate of 95%. Filtering out detections with confidence scores below 0.5 helped minimize false positives. Overall, the developed model effectively fulfills the need for fast and reliable object detection in restaurant service robots.

Recommendations for Improvement:

    Increase Data Diversity: Include datasets with varying angles, lighting conditions, and backgrounds.

    Hyperparameter Optimization: Perform more detailed tuning, e.g., via the hyp.scratch.yaml file.

    Prevent Overfitting: Enhance generalization using data augmentation techniques such as rotation and brightness adjustment.

    Real-Time Optimization: Employ model acceleration tools like TensorRT to improve performance in real-time applications.

Prepared by: Melih Can Orel
Contact: orelmelihcan@gmail.com
