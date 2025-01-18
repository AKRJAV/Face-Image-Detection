# Face Image Detection and Recognition using OpenCV and Face Recognition

## Project Overview
This Python-based application utilizes **OpenCV** and the **face_recognition** library to perform face detection and recognition. The program allows users to upload images for comparison against a preloaded database of known face images. The application detects faces, encodes them, and attempts to find a match from the database. Results are displayed with bounding boxes around detected faces, and if a match is found, a side-by-side comparison of the uploaded image and the matched image is shown.

## Features
- **Face Detection**: Detects faces in images and highlights them with bounding boxes.
- **Face Recognition**: Compares uploaded images with a set of known images and identifies matches.
- **Interactive Upload**: Users can upload images during runtime for dynamic face recognition.
- **Side-by-Side Comparison**: Displays the uploaded image alongside the matched image (if found).
- **Color-Coded Bounding Boxes**: Green boxes indicate matches, red boxes indicate no match.
- **Exit Condition**: Allows the user to type 'exit' to quit the application.

## Libraries Used
- **OpenCV**: For image processing tasks such as loading, resizing, and displaying images, as well as drawing bounding boxes around detected faces.
- **face_recognition**: A library built on dlib, used for detecting and encoding faces, as well as comparing face encodings to identify matches.
- **Google Colab**: Utilized for file uploads (`files.upload()`) and displaying images in the Colab environment (`cv2_imshow`).

## How It Works

1. **Image Upload**:
   - The user uploads an image for face recognition.
   - If the user types "exit", the program terminates.

2. **Face Detection and Encoding**:
   - The uploaded image is processed to detect faces using **face_recognition.face_locations()**.
   - The detected faces are encoded using **face_recognition.face_encodings()**.

3. **Face Matching**:
   - The uploaded image's face encoding is compared against preloaded face encodings from a specified folder.
   - If a match is found, the program retrieves the corresponding known image and prepares it for display.

4. **Result Display**:
   - A bounding box is drawn around each detected face in the uploaded image.
   - If a match is found, the name of the matched person is displayed along with the side-by-side comparison of the uploaded and matched images.
   - If no match is found, the uploaded image is displayed with the message "No Match Found".

## Code Explanation

### 1. **Installation**:
To install the required libraries, run the following commands:
```bash
!pip install face_recognition
!pip install opencv-python

```
### 2. **Resizing Image**:
A function "resize_image" is defined to resize an image to a target height while maintaining the aspect ratio:
```bash
!pip install face_recognition
!pip install opencv-python
