# URECA Project: Gauze Detection and Counting

This repository contains the implementation of a real-time gauze detection and counting system using YOLOv5 and YOLOv7. The project was developed as part of the URECA (Undergraduate Research Experience on Campus) program.

## Project Overview

The system uses computer vision and deep learning to detect and count gauze pads in real-time video streams. It can handle multiple camera inputs and provides accurate counting with hand detection capabilities.

## Features

- Real-time gauze detection and counting
- Multiple camera support
- Hand detection for interaction
- FPS monitoring
- Threaded video capture for improved performance
- Support for both YOLOv5 and YOLOv7 models

## Project Structure

- `yolov5/` - YOLOv5 implementation and models
- `yolov7/` - YOLOv7 implementation and models
- `ureca_images/` - Dataset and training images
- `Current YoloV5 Code.ipynb` - Main implementation notebook
- `latest yolo.ipynb` - Latest version of the implementation
- `yolov5-master/iGauze_Counter_v2.ipynb` - Threaded implementation

## Requirements

- Python 3.8+
- PyTorch
- OpenCV
- YOLOv5/YOLOv7 dependencies

## Usage

1. Clone the repository
2. Install dependencies
3. Run the desired notebook:
   - For standard implementation: `Current YoloV5 Code.ipynb`
   - For threaded implementation: `iGauze_Counter_v2.ipynb`

## Model Files

The repository includes several trained models:
- `2 Categories Yolov5.pt`
- `2 Categories Yolov7.pt`
- `2 Categories Yolov8.pt`

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- URECA program
- YOLOv5 and YOLOv7 teams for their excellent work
- All contributors to the project 