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
def resize_image(image, target_height):
    """Resize an image to a target height while maintaining aspect ratio."""
    h, w = image.shape[:2]
    aspect_ratio = w / h
    target_width = int(target_height * aspect_ratio)
    return cv2.resize(image, (target_width, target_height))

```
### 3. **Loading Face Encodings**:
The "load_face_encodings" function loads images from a folder, detects faces, and generates face encodings:
```bash
def load_face_encodings(folder_path):
    encodings = []
    names = []
    for filename in os.listdir(folder_path):
        if filename.lower().endswith(('.jpg', '.jpeg')):
            image_path = os.path.join(folder_path, filename)
            img = cv2.imread(image_path)
            rgb_img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
            face_encodings = face_recognition.face_encodings(rgb_img)
            if face_encodings:
                encodings.append(face_encodings[0])
                names.append(filename.split('.')[0])
    return encodings, names

```
### 4. **Main Loop**:
The main loop allows users to upload images for comparison. It then compares the uploaded image against preloaded face encodings and displays the result:
```bash
while True:
    uploaded = files.upload()
    uploaded_image_name = list(uploaded.keys())[0]

    if uploaded_image_name.lower() == 'exit':
        break

    img_to_compare = cv2.imread(uploaded_image_name)
    rgb_img_to_compare = cv2.cvtColor(img_to_compare, cv2.COLOR_BGR2RGB)
    img_to_compare_encoding = face_recognition.face_encodings(rgb_img_to_compare)

    match_found = False
    matched_name = "Unknown"

    if img_to_compare_encoding:
        for encoding, name in zip(encodings, names):
            if face_recognition.compare_faces([encoding], img_to_compare_encoding[0])[0]:
                match_found = True
                matched_name = name
                break

    # Draw bounding box and display matched image
    face_locations = face_recognition.face_locations(rgb_img_to_compare)
    for (top, right, bottom, left) in face_locations:
        color = (0, 255, 0) if match_found else (0, 0, 255)
        cv2.rectangle(img_to_compare, (left, top), (right, bottom), color, 2)
        cv2.putText(img_to_compare, matched_name, (left, top - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.9, color, 2)
    
    # Show the result
    cv2_imshow(img_to_compare)
```

### **Face Identification Sample Images**

## Image 1
![image](https://github.com/user-attachments/assets/c8e1f6b1-8f40-4961-bacd-27e83d97c7f3)


