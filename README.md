# VAT-score-calculation

This repository contains the implementation of a **VAT (Visual-Auditory-Textual) Score Calculation**, developed as part of our **Final Year B.Tech Project** —  **Genetic Algorithm-based Adaptive E-Learning Platform** which is designed to deliver personalized elearning experiences.

**VAT stands for Visual, Auditory, and Textual learning modalities** are the three primary channels through which educational content is consumed. This VAT Score Calculator is a tool that analyzes educational content and computes scores that quantify the visual, auditory, and textual richness of the content.

## Auditory Score

- **Objective**: Evaluate how engaging or content-rich the audio track of the video is.
- **Steps**:
  1. **Audio Extraction**:
     - Audio is extracted using libraries like `moviepy` or `ffmpeg`.
  2. **Feature Analysis**:
     - Audio features such as **energy**, **pitch variance**, **spectral roll-off**, and **MFCCs** will be computed using `librosa` or `pyAudioAnalysis`.
  3. **Scoring Logic**:
     - More varied and dynamic audio (indicating active instruction or dialogue) receives a higher score.
     - The score is normalized between 0 and 1.
    
## Textual Score

- **Objective**: Determine how much textual (spoken or visible) educational content is present.
- **Steps**:
  1. **Speech-to-Text Conversion**:
     - Transcription of audio using online transcribers.
  2. **Text Analysis**:
     - Metrics such as **word density**, **keyword frequency**, and **reading ease** will be calculated using NLP.
     - Presence of domain-specific educational terms is scored positively.
  3. **Score Calculation**:
     - A composite score is created based on clarity, content density, and relevance.
     - This score is also normalized between 0 and 1.
    
## Visual Score

- **Objective**: Measure how visually rich or informative a video is.
- **Steps**:
  1. **Frame Extraction**:
     - The video is sampled using OpenCV at regular intervals (e.g., every 30 frames).
  2. **Pretrained Model**:
     - Each sampled frame is passed through a **ResNet-18** model (from `torchvision.models`) pretrained on ImageNet.
  3. **Prediction Confidence**:
     - For each frame, the **top predicted class and its probability** are extracted.
  4. **Score Aggregation**:
     - A higher confidence in a meaningful class (e.g., “blackboard”, “laptop”, “classroom”) implies a richer frame.
     - Visual scores from all frames are averaged to obtain the **final Visual Score**.


## 🧠 Use Case in Adaptive Learning

- These VAT scores help classify the learning content as **visually**, **auditorily**, or **textually** dominant.
- This system supports **personalized e-learning experiences** by aligning content characteristics with cognitive preferences.
