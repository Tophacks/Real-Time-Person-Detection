# Real-Time Person Detection

A desktop computer-vision application that uses a webcam to detect people in real time. The project is built with Python, OpenCV, and Tkinter and uses OpenCV's HOG (Histogram of Oriented Gradients) descriptor with the default SVM people detector.

## Features

- Real-time webcam capture with OpenCV
- Person detection using HOG + SVM
- Bounding boxes around detected people
- Desktop interface built with Tkinter
- Start and stop camera controls
- Detection status indicator
- Audible alert when a person is detected
- Separate producer and consumer threads for video capture and processing
- Bounded frame queue to keep the application responsive
- Performance optimization by resizing frames and processing every third frame

## How It Works

The application separates camera capture from computer-vision processing.

1. A producer thread continuously captures frames from the webcam.
2. Captured frames are placed into a bounded queue.
3. A consumer thread retrieves frames and processes every third frame.
4. Frames are resized before detection to reduce processing cost.
5. OpenCV's HOG descriptor and default SVM people detector search for pedestrians.
6. Detected people are highlighted with bounding boxes and the interface displays an alert.

Using a bounded queue allows frames to be dropped when processing falls behind rather than allowing latency to grow indefinitely.

## Tech Stack

- **Python**
- **OpenCV**
- **Tkinter**
- **Pillow (PIL)**
- **threading**
- **queue**
- **winsound**

## Requirements

This project currently uses `winsound`, so the audible alert is intended for Windows.

Install the required Python packages:

```bash
pip install opencv-python pillow
```

Tkinter is included with most standard Python installations.

## Running the Project

Clone the repository:

```bash
git clone https://github.com/Tophacks/real-time-person-detection.git
cd real-time-person-detection
```

Run:

```bash
python main.py
```

Make sure a webcam is connected and available to OpenCV.

## Current Implementation

The detector uses OpenCV's classical HOG + SVM pedestrian-detection pipeline rather than a neural-network model. The project focuses on real-time video processing, concurrency, UI integration, and computer-vision application design.

## Possible Improvements

Future improvements could include:

- Replacing HOG + SVM with a modern object detector such as YOLO
- Supporting multiple object classes
- Adding configurable confidence thresholds
- Saving detection events and timestamps
- Recording short clips when detections occur
- Improving cross-platform audio alerts
- Adding automated tests and performance benchmarks

## Author

**Nathaniel (Nate) Powell**
