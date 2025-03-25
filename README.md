
# Audio Extraction and Speech-to-Text Transcription

This project demonstrates how to extract audio from a video file and perform speech-to-text transcription using **FFmpeg** and **SpeechRecognition** in Python.

---

## 📋 Features
1. **Audio Extraction**: Extract audio from a video file using FFmpeg.
2. **Speech-to-Text Transcription**: Convert the extracted audio into text using Google's Speech Recognition API.

---

## 📂 Directory Structure
```
.
├── video.mp4              # Input video file
├── audio.wav              # Extracted audio file
└── transcript.txt         # File to save the transcription (optional)
```

---

## ⚙️ Installation

### 1. Install FFmpeg
FFmpeg is required to extract audio from video files. Install FFmpeg using the following commands:

- On **Ubuntu/Linux**:
  ```bash
  sudo apt update
  sudo apt install ffmpeg
  ```

- On **Windows**: Download FFmpeg from [FFmpeg Downloads](https://ffmpeg.org/download.html) and add it to the PATH.

### 2. Install Python Libraries
Install the required Python libraries:
```bash
pip install speechrecognition pydub
```

---

## 🚀 How to Use

### Step 1: Extract Audio from Video
Use FFmpeg to extract audio from a video file:
```bash
ffmpeg -i video.mp4 -q:a 0 -map a audio.wav
```

Alternatively, use the provided Python script:
```python
import subprocess

video_path = "/path/to/video.mp4"
audio_path = "/path/to/audio.wav"

command = ["ffmpeg", "-i", video_path, "-q:a", "0", "-map", "a", audio_path, "-y"]
subprocess.run(command, stdout=subprocess.PIPE, stderr=subprocess.PIPE)

print("Audio successfully extracted:", audio_path)
```

### Step 2: Perform Speech-to-Text Transcription
Transcribe the extracted audio to text:
```python
import speech_recognition as sr

audio_path = "/path/to/audio.wav"
recognizer = sr.Recognizer()

with sr.AudioFile(audio_path) as source:
    audio_data = recognizer.record(source)
    text = recognizer.recognize_google(audio_data, language="id-ID")

print("Transcription:
", text)
```

---

## 📊 Output
1. **Extracted Audio**: The extracted audio is saved as `audio.wav`.
2. **Transcription**: The transcription is printed to the console and can optionally be saved to a text file.

---

## 💡 Notes
1. Make sure the input video contains clear audio for better transcription results.
2. Ensure that FFmpeg is correctly installed and added to the system PATH.
3. The `SpeechRecognition` library uses the Google Speech API for transcription, which requires an active internet connection.

---

## 📬 Contact
If you have any questions or need assistance, feel free to reach out! 😊
