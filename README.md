# AgriScan : AI-Powered Bilingual Plant Disease Detection System

AgriScan is an edge-based agricultural intelligence system designed to detect plant diseases from leaf images and provide actionable, structured insights in both English and Hindi.

Unlike conventional plant disease classifiers that output only a predicted label, AgriScan functions as a knowledge-enriched decision support system built for real-world agricultural deployment.

---

# Executive Summary

AgriScan enables farmers and agricultural stakeholders to:

- Capture a photo of a plant leaf using a mobile device
- Detect disease instantly using a trained deep learning model
- Receive structured scientific information about the disease
- Understand causes, symptoms, treatment, prevention, and economic impact
- Access results in Hindi or English
- Operate fully offline with local inference

The system integrates:

- A trained deep learning model (TensorFlow/Keras)
- ONNX-based optimized local inference
- A bilingual JSON-driven knowledge engine
- A mobile-first APK application built with TypeScript, JavaScript, and CSS

---

# Problem Statement

Crop diseases significantly impact agricultural productivity, particularly in regions where:

- Farmers lack immediate access to agronomists
- Scientific information is not readily accessible in local languages
- Internet connectivity is unreliable
- Most available tools are either cloud-dependent or English-only

Many academic and Kaggle-style machine learning projects focus solely on classification accuracy without addressing real-world deployment, accessibility, or advisory depth.

AgriScan bridges this gap by combining AI-based detection with structured agricultural intelligence in an offline-capable system.

---

# Proposed Solution

AgriScan implements a complete edge-AI diagnostic pipeline:

1. User captures or uploads a leaf image  
2. Image is resized and normalized locally  
3. ONNX model performs inference on-device  
4. Predicted class and confidence score generated  
5. Disease metadata retrieved via bilingual JSON mapping  
6. Results rendered with severity indication and advisory guidance  

All processing occurs locally without any server or API dependency.

---

# System Architecture

## High-Level Workflow

| Step | Component                     | Description                                                                 |
|------|--------------------------------|-----------------------------------------------------------------------------|
| 1    | Camera / Image Upload         | User captures a leaf image using device camera or uploads from gallery.   |
| 2    | Image Preprocessing           | Image resized to 128×128 and normalized before inference.                  |
| 3    | ONNX Model Inference          | Optimized ONNX model performs local prediction on the device.              |
| 4    | Class Prediction + Confidence | Model outputs predicted disease class along with confidence score.         |
| 5    | JSON Knowledge Engine         | Disease metadata retrieved from bilingual (English/Hindi) JSON mapping.    |
| 6    | Bilingual UI Rendering        | Final results displayed with severity, advisory, and language selection.   |


---

## Architecture Components

### 1. Mobile Application Layer
- TypeScript
- JavaScript
- CSS
- APK-based deployment
- Camera integration
- Image upload functionality

### 2. Machine Learning Layer
- Custom CNN model (TensorFlow/Keras)
- Model saved as `.h5`
- Converted to ONNX format
- Local inference execution

### 3. Knowledge Engine
- Structured JSON-based disease database
- English and Hindi content mapping
- Dynamic rendering based on language selection

### 4. UI/UX Layer
- Confidence score display
- Severity classification (e.g., Moderate, Severe)
- Disease explanation sections
- Profile and scan statistics
- Language toggle system

---

# Machine Learning Pipeline

## Dataset

- Source: PlantVillage (Tomato subset)
- Total Classes: 10 (9 diseases + 1 healthy)
- Approximate Dataset Size: 18,000+ images
- Balanced class distribution
- **Source**: [Kaggle](https://www.kaggle.com/datasets/ashishmotwani/tomato)
- **Description**: The dataset contains over 20,000 images of tomato leaves with 10 diseases and 1 healthy class. Images are collected from both lab scenes and in-the-wild scenes.
- **Goal**: The objective is to develop a lightweight model that can predict tomato leaf disease and be deployed offline on a mobile app.


## Data Split

- Training: 80%
- Validation: 20%

## Image Preprocessing

- Resize: 128 × 128
- Pixel normalization: image / 255.0
- Data augmentation:
  - Rotation
  - Width shift
  - Height shift
  - Horizontal flip
  - Zoom

---

## Model Architecture

- Custom Convolutional Neural Network (CNN)
- Stacked Conv2D + MaxPooling layers
- Fully connected dense layers
- Softmax output layer for multi-class classification

### Training Configuration

- Framework: TensorFlow + Keras
- Optimizer: Adam
- Loss Function: Categorical Crossentropy
- Epochs: 20
- Training Environment: GPU-enabled environment

---

# Performance Metrics

- Validation Accuracy: ~95%
- Precision: High across majority of classes
- Recall: Strong detection across disease categories
- F1-Score: Balanced and consistent
- Confusion Matrix: Minimal inter-class overlap
- Inference Time: Near real-time (sub-second on device)

---

# Edge Deployment Strategy

The trained `.h5` model is converted to ONNX to enable:

- Cross-platform compatibility
- Optimized local inference
- Low latency prediction
- Complete offline operation
- Data privacy preservation

Inference is executed locally within the application without external API calls.

---

# Application Features

## Core Functionalities

- Camera-based leaf scanning
- Image upload option
- Confidence percentage display
- Severity level indicator
- Instant diagnostic feedback

---

## Knowledge-Rich Advisory Output

For each detected disease, the system provides:

- Scientific name
- Disease history
- Symptoms
- Causes
- Treatment recommendations
- Preventive measures
- Economic impact analysis

This transforms the application from a classifier into a decision-support platform.

---
# Bilingual Intelligence Engine

- English and Hindi language support
- JSON-driven content mapping
- Dynamic UI rendering based on selection
- Designed specifically for rural accessibility

---
# User Module

- Profile dashboard
- Scan statistics tracking
- Healthy vs. issue breakdown
- Scan history logging

---
# Differentiation

## Compared to Typical Kaggle Projects

| Generic ML Demo | AgriScan |
|-----------------|----------|
| Label prediction only | Structured agricultural advisory |
| Notebook-based demo | Full mobile APK application |
| Cloud inference | Local ONNX inference |
| English-only | Bilingual support |
| Research prototype | Deployment-ready system |

## Compared to Generic Plant Apps

- Offline functionality
- Knowledge-enriched advisory output
- Economic impact explanation
- Multi-stakeholder design
- Scalable crop expansion architecture

---
# Target Users

- Small-scale farmers
- Agricultural startups
- Government agricultural extension services
- Field inspection officers

---

# Repository Structure


| Directory / File | Description |
|------------------|-------------|
| `Agriscan/` | Root directory of the project |
| `model/` | Contains trained and deployment-ready models |
| ├── `model.h5` | Original trained TensorFlow/Keras model |
| ├── `model.onnx` | Converted ONNX model for optimized local inference |
| `app/` | Application source code (UI + integration layer) |
| ├── `src/` | Core application logic and entry points |
| ├── `components/` | Reusable UI components |
| ├── `assets/` | Static assets such as images, icons, styles |
| `knowledge_base/` | Structured disease information storage |
| ├── `diseases_en.json` | English disease metadata mapping |
| ├── `diseases_hi.json` | Hindi disease metadata mapping |
| `notebook/` | Model training and experimentation environment |
| ├── `training_notebook.ipynb` | Complete ML training pipeline notebook |
| `apk/` | Android build output |
| ├── `Agriscan.apk` | Installable Android application file |
| `README.md` | Project documentation |

---

# Installation Guide

1. Clone the repository  
2. Install required dependencies  
3. Ensure the ONNX model file is available  
4. Run the application locally  
5. Build APK for Android deployment  

---

# Future Scope

- Expansion to multi-crop disease detection
- Weather-based predictive risk alerts
- Fertilizer and pesticide optimization engine
- AI-based conversational agricultural assistant
- Market price integration
- Government agricultural data integration
- Satellite-based crop health monitoring

---
# Scalability Vision

AgriScan is designed for scalable agricultural deployment including:

- Nationwide integration
- Collaboration with agricultural extension services
- Integration with AgriTech startups
- Rural digital empowerment initiatives

---

# Application Screenshots

![WhatsApp Image 2026-02-13 at 11 53 01 AM](https://github.com/user-attachments/assets/f8dd660a-0221-442f-a2cb-310e60910e32)
![WhatsApp Image 2026-02-13 at 11 52 02 AM](https://github.com/user-attachments/assets/4f91d3c6-9621-4c2f-9794-0d0fdc9d69f8)
![WhatsApp Image 2026-02-13 at 11 51 33 AM](https://github.com/user-attachments/assets/13eb982a-88e9-450d-a909-28e3164063eb)
![WhatsApp Image 2026-02-13 at 11 51 03 AM](https://github.com/user-attachments/assets/250b8f8c-2730-4b31-b136-d6e4d5fd2ad4)
![WhatsApp Image 2026-02-13 at 11 50 03 AM](https://github.com/user-attachments/assets/c19219d3-4db1-4403-a91a-e49b23714a7a)
![WhatsApp Image 2026-02-13 at 11 49 54 AM](https://github.com/user-attachments/assets/0d0cf24a-b539-4436-9d70-a081b8e24824)
![WhatsApp Image 2026-02-13 at 11 49 54 AM (1)](https://github.com/user-attachments/assets/78169082-4fe5-4dc3-836e-1a548f98a54e)
![WhatsApp Image 2026-02-13 at 11 49 53 AM](https://github.com/user-attachments/assets/9ba9aa1c-9290-440e-a41f-179297a4857e)
![WhatsApp Image 2026-02-13 at 6 01 33 PM](https://github.com/user-attachments/assets/c6514307-bd40-4d13-96f6-7045c035ad2a)


- Home Screen  
- Scan Result Screen  
- Disease Detail Page (Hindi)  
- Profile Dashboard  
- Statistics Overview  

---

# Developers

- Name: Abhinav Mehra
- Role: Developer 
- Contact: https://www.linkedin.com/in/abhinav-mehra-356a7a333

---

# Contributors

- Name:  Himanshu Gaur 
- Contribution Area: Developer 
- Contact:  https://www.linkedin.com/in/himanshu-gaur-305006282/

---


---
