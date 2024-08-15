# AI Engineer Intern Knowledge Test - Vehicle Counter System

## Introduction

Hello! 👋👋
I'm currently applying for an AI Engineer Intern position at Widya Robotics through the MSIB Batch 7 program. As part of the recruitment process, I developed a vehicle counter system using deep learning. This project aims to count vehicles passing through a specific gate in a video, a task that is crucial for traffic monitoring, urban planning, and public safety.

## Objective

The vehicle counter system was built to:
- Read and process an input video.
- Detect vehicles (cars and buses) using a pre-trained YOLOv5 model.
- Track and assign unique IDs to detected vehicles as they move through the video frames.
- Count vehicles that cross a defined diagonal line in the video.
- Visualize the detected vehicles, IDs, and the vehicle count on the video output.
- Save the processed video for further analysis.

## System Requirements

This project was developed in Python using the following libraries:
- **YOLOv5**: For vehicle detection.
- **OpenCV**: For video processing and visualization.
- **PyTorch**: For loading and utilizing the YOLOv5 model.
- **Google Colab**: Used as the development and testing environment.

## Installation

To run this project, follow these steps:

1. Clone the YOLOv5 repository and install dependencies:

   ```
   !pip install -q git+https://github.com/ultralytics/yolov5.git
   ```

2. Upload your video file using Google Colab's file upload feature:

   ```
   from google.colab import files

   uploaded = files.upload()
   video_path = next(iter(uploaded))
   ```

3. Load the pre-trained YOLOv5 model:

   ```
   import torch

   model = torch.hub.load('ultralytics/yolov5', 'yolov5m', pretrained=True)
   ```

## Usage

Once the environment is set up, follow these steps to run the vehicle counter system:

1. Open the video file using OpenCV and process it frame by frame:

   ```
   import cv2

   cap = cv2.VideoCapture(video_path)
   ```

2. Detect vehicles in each frame using the YOLOv5 model:

   ```
   results = model(frame)
   detections = results.xyxy[0].cpu().numpy()
   ```

3. Track vehicles and count those that cross the defined diagonal line. The line is drawn from the top left to the bottom right of the frame:

   ```
   cv2.line(frame, line_start, line_end, (0, 0, 255), 2)
   ```

4. Save the output video with bounding boxes, labels, and vehicle count:

   ```
   out.write(frame)
   ```

5. Download the output video file once processing is complete:

   ```
   files.download(output_video_path)
   ```

## How It Works

- **Vehicle Detection**: YOLOv5 is used to detect vehicles in each video frame. The model identifies objects of class 'car' and 'bus'.
- **Tracking & Counting**: Each detected vehicle's bounding box center is monitored, and if it crosses the diagonal line defined in the frame, it is counted.
- **Visualization**: Bounding boxes and the vehicle count are drawn onto the video frames, providing visual feedback of the system's performance.
- **Output Video**: The system saves the processed frames into a video file, which can be downloaded and reviewed later.

## Conclusion

This project demonstrates my ability to implement a deep learning-based computer vision system for vehicle detection and counting. I hope this showcases my skills and potential contributions as an AI Engineer Intern at Widya Robotics.

---

