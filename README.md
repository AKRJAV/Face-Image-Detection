# Face Image Detection with OpenCV and Face Recognition

Project Overview
This Python-based face recognition application uses OpenCV and face_recognition libraries to detect and identify faces in images. It allows users to upload images dynamically for comparison against a preloaded database of known faces. The application provides visual feedback by displaying bounding boxes around detected faces and showing side-by-side comparisons of the uploaded and matched images.

Features
Face Detection: Identifies and localizes faces in images.
Face Recognition: Matches uploaded face images against a pre-existing database of known faces.
Dynamic Uploads: Accepts user-uploaded images during runtime for real-time processing.
Visualization: Displays results with bounding boxes and side-by-side matched image comparisons.
Interactive Interface: Provides prompts for user uploads and displays match status.
Workflow
Preprocessing:

Loads all images from a specified folder and encodes the faces using face_recognition.
Stores the encodings along with corresponding names derived from the image filenames.
User Interaction:

Prompts the user to upload an image for comparison.
Dynamically processes the uploaded image to detect and encode faces.
Face Matching:

Compares the uploaded image's face encoding to the preloaded database using face_recognition.compare_faces.
Identifies a match if the similarity meets the threshold.
Visualization:

Draws bounding boxes on the uploaded image to mark detected faces.
If a match is found, displays the name of the matched person and a side-by-side view of the uploaded and matched images.
Outputs a status message indicating whether a match was found.
Libraries Used
OpenCV: For reading, resizing, and displaying images.
face_recognition: For face detection, encoding, and comparison.
Google Colab Integration:
files.upload: To upload images for comparison.
cv2_imshow: To display images interactively.
Example Workflow
Load Known Faces:

Place known face images in a folder (e.g., Image_Recognition) with filenames representing the person’s name (e.g., John.jpg).
Upload an Image:

The application prompts the user to upload an image for comparison.
Detection and Recognition:

The program detects faces in the uploaded image and compares them with the known face encodings.
Result:

If a match is found:
The name of the matched person is displayed.
A side-by-side comparison of the uploaded and matched images is shown.
If no match is found, the uploaded image is displayed with a "No Match Found" message.
Limitations
The application currently supports one face per image for recognition.
Performance may degrade with large databases of face encodings.
Lighting conditions and image quality can impact accuracy.
Future Enhancements
Add support for multi-face detection and recognition in a single image.
Extend functionality for real-time video processing.
Improve scalability by integrating a database for face storage.
Develop a GUI for better user experience.
