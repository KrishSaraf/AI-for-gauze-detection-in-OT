# AI-for-gauze-detection-in-OT

**Smart Operation Theatre: Automated Gauze Detection and Counting using YOLOv7**

## Project Overview

This project aims to enhance surgical safety by automating the detection and counting of medical gauzes during operations. Retained surgical items, such as gauzes, can lead to severe complications (gossypiboma). Our system leverages computer vision and deep learning (YOLOv7) to provide real-time monitoring and counting of gauzes, reducing human error and improving workflow efficiency in the operating theatre.

## Key Features

- **Dual-Tray System:** Tracks both unused ("In") and used ("Out") gauzes in real time.
- **YOLOv7-based Detection:** Trained to identify gauzes and hands under various lighting and placement conditions.
- **Real-Time Counting:** Continuously updates the count of gauzes on each tray and flags discrepancies.
- **Threaded Video Processing:** Uses Python threading to process multiple video streams simultaneously, ensuring high FPS and low latency.
- **User Interface:** Displays live video feeds, detection results, and ongoing counts for both trays.

## Methodology

1. **Data Collection:**  
   Images and videos of gauze manipulation in a dual-tray system were collected under diverse conditions (lighting, occlusion, etc.).
2. **Data Annotation & Augmentation:**  
   Images were labeled for gauze and hand detection, then augmented to increase dataset size and robustness.
3. **Model Training:**  
   The YOLOv7 model was trained using the annotated dataset. The trained weights are saved in the file:
   - **`yolov7.pt`** (not included in the repository due to size; see below for download instructions)
4. **Real-Time Application:**  
   A Python application loads the trained weights and processes live video feeds from two cameras (one for each tray). Threading is used to handle both video streams in parallel, significantly improving processing speed and ensuring real-time performance.
5. **Counting Logic:**  
   The system tracks the number of gauzes on each tray, updating "In", "Out", and "In Play" counts. It alerts if there is a mismatch at the end of the operation, helping prevent retained gauzes.

## File Structure

```
.
├── yolov7/                # YOLOv7 codebase (detection scripts, model definition, etc.)
├── yolov7.pt              # Trained model weights (not included in repo, see below)
├── *.ipynb                # Jupyter notebooks for training, testing, and analysis
├── *.py                   # Python scripts for detection, counting, and threading
├── yolo_gauze.yml         # Dataset configuration file
├── README.md              # Project documentation
├── LICENSE                # License file
└── .gitignore             # Git ignore rules (excludes large files, model weights, etc.)
```

## Model Weights

- **File:** `yolov7.pt`
- **Purpose:** Contains the trained YOLOv7 model weights for gauze and hand detection.
- **Usage:** The detection and counting scripts load this file to perform inference on live or recorded video streams.
- **Note:** This file is not included in the repository due to GitHub's file size limits.  
  **To obtain the weights:**  
  - Download from [Google Drive / S3 / your link here]  
  - Place the file in the project root directory.

## How Threading Improves Speed

The system uses Python's `threading` module to process video streams from both the "In" and "Out" trays simultaneously. This parallel processing allows:
- Real-time detection and counting on both trays without lag.
- Higher frames-per-second (FPS) performance, crucial for live surgical environments.
- Efficient use of system resources, as detection and UI updates run concurrently.

## Usage

1. **Clone the repository:**
   ```bash
   git clone https://github.com/KrishSaraf/AI-for-gauze-detection-in-OT.git
   cd AI-for-gauze-detection-in-OT
   ```
2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
3. **Download model weights:**  
   Place `yolov7.pt` in the project root as described above.
4. **Run the detection/counting script:**
   ```bash
   python detect.py
   ```
   (Or use the provided Jupyter notebooks for experimentation.)

## Results

- **Live Monitoring:** The system displays two live video feeds, one for each tray, with bounding boxes and confidence scores for detected gauzes and hands.
- **Counting Logic:**  
  - "On Screen" shows the current number of gauzes visible on each tray.
  - "Total In" and "Total Out" track the cumulative number of gauzes processed.
  - "In Play" indicates the number of gauzes unaccounted for (should be zero at the end).
- **Performance:** Achieves real-time detection with high accuracy and FPS, as demonstrated in live trials.

## Clinical Significance

- Reduces the risk of retained gauzes (gossypiboma).
- Minimizes manual counting errors and improves workflow.
- Designed in collaboration with Singapore General Hospital (SGH) for real-world applicability.

## Future Work

- Integrate a TV screen for easier monitoring in the OT.
- Expand dataset and improve model robustness.
- Deploy and test in more live surgeries for further validation.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Nanyang Technological University, Singapore
- Singapore General Hospital (SGH)
- Supervisors: Dr. Cai Yiyu, Dr. Huang Li Hui, Abu Bakr Azam 