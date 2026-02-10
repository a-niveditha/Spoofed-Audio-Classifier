# Spoofed-Audio-Classifier
This repository consists the spoofed dataset, and a LCNN based classifier for the same. 
---
## Dataset

### Original Audio
We use the **IndicVoices** dataset by AI4Bharat for original speech samples:

https://huggingface.co/datasets/ai4bharat/IndicVoices

### Spoofed Audio
Spoofed samples are created by replaying the original audio under different:
- Playback devices  
- Recording devices  
- Distances  
- Angles  
- Acoustic environments  

---

## Features
- Audio is split into overlapping chunks:
  - Window size: 3 seconds
  - Hop size: 1 second

---

## Model

- **LCNN (Light CNN)** with Max-Feature-Map (MFM) activations
- Trained for binary classification:
  - 0 → Original
  - 1 → Spoofed

---

## Training

- Chunk-level training
- Binary cross-entropy loss
- Adam optimizer
- Best model saved based on validation accuracy
- No data leakage (splits are done at original-file level)

---

## Evaluation

Evaluation is done at **file level** by aggregating chunk predictions.

Metrics reported:
- File-level Accuracy
- File-level Error Rate
- Equal Error Rate (EER)
- EER Threshold
