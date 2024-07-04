# License Plate Detection and Recognition System

This repository contains a Python-based application that detects license plates in images using a YOLO (You Only Look Once) model and recognizes the text on these plates using Tesseract OCR. The application uses OpenCV for image processing and Flask for the web interface.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Files](#files)
- [Functions](#functions)
- [Web Interface](#web-interface)
- [Acknowledgements](#acknowledgements)

## Installation

1. **Clone the repository:**
   ```sh
   git clone https://github.com/yourusername/LicensePlateDetection.git
   cd LicensePlateDetection
   ```

2. **Create a virtual environment:**
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. **Resulting App:**
  ![image](https://github.com/Sojournes/Automatic-License-Plate-Detector/assets/97471046/66fbdcdb-950d-4bff-b746-d0fab6f8081e)


4. **Download the YOLO model:**
   Ensure you have the `best.onnx` model file in the `static/models/` directory.

5. **Install Tesseract:**
   - **Windows:** Download the installer from [here](https://github.com/UB-Mannheim/tesseract/wiki).
   - **Linux:** Install via your package manager, e.g., `sudo apt-get install tesseract-ocr`.
   - **macOS:** Install via Homebrew, e.g., `brew install tesseract`.

## Usage

To start the Flask application, run:

```sh
python app.py
```

Then, open your browser and navigate to `http://127.0.0.1:5000/` to access the web interface.

## Files

- `app.py`: The main Flask application file.
- `deeplearning.py`: Contains functions for object detection and text extraction.
- `templates/index.html`: The HTML template for the web interface.
- `static/models/best.onnx`: The YOLO model file.
- `static/upload/`: Directory where uploaded images are saved.
- `static/predict/`: Directory where prediction results are saved.

## Functions

### 1. `get_detections(img, net)`

Converts an image to YOLO format, processes it using the YOLO model, and returns the processed image and detections.

### 2. `non_maximum_supression(input_image, detections)`

Filters detections based on confidence and probability scores and applies Non-Maximum Suppression (NMS) to remove redundant bounding boxes.

### 3. `extract_text(image, bbox)`

Extracts text from a given bounding box in the image using Tesseract OCR.

### 4. `drawings(image, boxes_np, confidences_np, index)`

Draws bounding boxes and recognized text on the image.

### 5. `yolo_predictions(img, net)`

Performs object detection, applies NMS, and draws results on the image.

### 6. `object_detection(path, filename)`

Reads an image, performs YOLO predictions, saves the result, and returns the recognized text list.

### 7. `apply_brightness_contrast(input_img, brightness=0, contrast=0)`

Applies brightness and contrast adjustments to the image.

## Web Interface

The web interface allows users to upload an image, which is then processed to detect and recognize license plates. The results are displayed on the web page, including the processed image and the recognized text.

### Flask Routes

- **`/` (GET, POST)**: The main route that handles image upload and displays results.

## Acknowledgements

This project uses:
- [OpenCV](https://opencv.org/) for image processing.
- [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) for text recognition.
- [YOLO](https://pjreddie.com/darknet/yolo/) for object detection.
- [Flask](https://flask.palletsprojects.com/) for the web interface.

Feel free to contribute to this project by submitting issues or pull requests.

---

Ensure that the paths in the code are correctly set up based on your project directory structure. Adjust the Flask application to suit your deployment environment if necessary.
