# face-detection-opencv

Facial Recognition Attendance Tracker built with OpenCV, `face_recognition`, and Firebase.
The app detects faces in real-time from webcam input and marks attendance for known users.

## Architecture Diagram

![Architecture Diagram](Generated%20Image%20February%2023,%202026%20-%207_55PM.png)

## Features

- Face detection + recognition using precomputed encodings.
- Real-time webcam monitoring.
- Firebase Realtime Database integration for student metadata and attendance.
- Firebase Cloud Storage integration for student profile images.
- OpenCV/cvzone dashboard UI with status modes.
- Attendance update cooldown logic to prevent duplicate marking.

## Project Flow

1. `add-data-database.py` seeds student metadata into Realtime Database.
2. `EncodeGenerator.py` uploads student images and builds `encodeFile.p`.
3. `main.py` loads encodings, runs webcam recognition, fetches student info, and updates attendance.

## Repository Structure

- `main.py`: Main runtime loop for recognition + UI + attendance update.
- `EncodeGenerator.py`: Enrollment script (image upload + embedding generation).
- `add-data-database.py`: Realtime Database seed data script.
- `images/`: Input student images used for encoding.
- `resources/background.png`: Background UI canvas.
- `resources/models/`: UI mode cards used by the dashboard.
- `encodeFile.p`: Serialized face encodings + student IDs.

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/K-SAHASRA/face-detection-opencv.git
   cd face-detection-opencv
   ```
2. Install dependencies:
   ```bash
   pip install opencv-python face-recognition cvzone firebase-admin numpy
   ```
3. Add your Firebase service account key file and update scripts if needed:
   - Current scripts expect `serviceAccountKey.json`.
4. Ensure Firebase resources exist:
   - Realtime Database path: `students/{id}`
   - Cloud Storage path for images: `images/{id}.jpg`

## Run

1. Seed metadata:
   ```bash
   python add-data-database.py
   ```
2. Generate encodings:
   ```bash
   python EncodeGenerator.py
   ```
3. Start attendance tracker:
   ```bash
   python main.py
   ```
4. Press `d` to exit.

## Acknowledgments

- OpenCV
- face_recognition
- cvzone
- Firebase
