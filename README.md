# Real-time Number Plate Recognition

## Overview
This project aims to develop a real-time number plate recognition system using computer vision techniques. It leverages the YOLOv8 model for vehicle and license plate detection, combined with the SORT algorithm for tracking vehicles across frames. The system processes video input (or a live camera feed) to detect vehicles, identify license plates, and extract license plate text, storing the results in a CSV file.

⚠️ **Note**: This project is still in development. The license plate detection model (`license_plate_detector.pt`) has not been trained yet, and the system is not fully operational.

## Features
- **Vehicle Detection**: Uses YOLOv8 (`yolov8n.pt`) to detect vehicles in video frames.
- **Vehicle Tracking**: Implements the SORT algorithm to track vehicles across frames.
- **License Plate Detection**: A placeholder YOLO model (`license_plate_detector.pt`) is used for detecting license plates (training pending).
- **License Plate Text Recognition**: Processes license plate images to extract text (requires a trained model for optimal performance).
- **Output**: Saves detection and recognition results, including vehicle and license plate bounding boxes, license plate text, and confidence scores, to a CSV file.

## Prerequisites
To run the project, you need the following dependencies:
- Python 3.8+
- OpenCV (`cv2`)
- Ultralytics YOLO (`ultralytics`)
- NumPy
- SORT algorithm (`sort.sort`)

Install the required packages using:
```bash
pip install opencv-python ultralytics numpy
```

Additionally, clone the SORT repository or include it as a submodule:
```bash
git clone https://github.com/abewley/sort.git
```

## Project Structure
- `main.py`: Main script for processing video input, detecting vehicles and license plates, tracking vehicles, and extracting license plate text.
- `util.py`: Contains utility functions for:
  - `get_car`: Associates a license plate with a tracked vehicle.
  - `read_license_plate`: Processes license plate images to extract text.
  - `write_csv`: Saves results to a CSV file.
- `models/license_plate_detector.pt`: Placeholder for the custom-trained YOLO model for license plate detection (not yet trained).
- `sample.mp4`: Sample video file for testing (replace with your own video or use a camera feed).
- `test.csv`: Output file containing detection and recognition results.

## Usage
1. **Prepare the Environment**:
   - Ensure all dependencies are installed.
   - Place the `yolov8n.pt` model in the project directory (available from Ultralytics).
   - Add a video file (`sample.mp4`) or modify `main.py` to use a camera feed by replacing `cv2.VideoCapture('sample.mp4')` with `cv2.VideoCapture(0)`.

2. **Run the Script**:
   ```bash
   python main.py
   ```
   The script processes the input video, detects vehicles and license plates, tracks vehicles, and attempts to read license plate text. Results are saved to `test.csv`.

3. **Output Format**:
   The output CSV (`test.csv`) contains frame-by-frame results with the following structure:
   - Frame number
   - Car ID
   - Vehicle bounding box (`[x1, y1, x2, y2]`)
   - License plate bounding box (`[x1, y1, x2, y2]`)
   - License plate text
   - Bounding box confidence score
   - Text recognition confidence score

## Current Limitations
- The license plate detection model (`license_plate_detector.pt`) is not yet trained, so license plate detection is not functional.
- License plate text recognition may not work reliably without a trained model.
- The system is designed for specific vehicle classes (YOLO class IDs: 2, 3, 5, 7 for cars, motorcycles, buses, and trucks).
- Performance depends on the quality of the input video and lighting conditions.

## Next Steps
- **Train the License Plate Detection Model**: Create and train a custom YOLO model for license plate detection.
- **Improve Text Recognition**: Integrate a robust OCR model (e.g., EasyOCR or Tesseract) for better license plate text extraction.
- **Optimize Performance**: Enhance processing speed for real-time applications.
- **Testing**: Validate the system with diverse video inputs and real-world scenarios.
- **Documentation**: Expand documentation with training instructions and detailed usage examples.

## Contributing
Contributions are welcome! Please feel free to:
- Submit issues for bugs or feature requests.
- Create pull requests for code improvements or new features.
- Help with training the license plate detection model or improving text recognition.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contact
For questions or suggestions, please open an issue on the GitHub repository.
