# AgriScan: Smart Leaf Disease Detection System

**AgriScan: Smart Leaf Disease Detection System** is a project created for farmer welfare. Designed to resolve the issue of plant diseases, it uses leaf-based disease detection.

The proposed mobile application will be a tool featuring an intuitive UI with features dedicated towards:
* Educating farmers about how to prevent crop wastage.
* Ensuring a healthier and more bountiful yield.

---

## Datasets to be used

### Plant Disease Dataset
* **Source**: [Kaggle](https://www.kaggle.com/datasets/ashishmotwani/tomato)
* **Description**: The dataset contains over 20,000 images of tomato leaves with 10 diseases and 1 healthy class. Images are collected from both lab scenes and in-the-wild scenes.
* **Goal**: The objective is to develop a lightweight model that can predict tomato leaf disease and be deployed offline on a mobile app.

---

## Disease Classes

* Late_blight
* healthy
* Early_blight
* Septoria leaf spot
* Tomato Yellow Leaf Curl Virus
* Bacterial_spot
* Target_Spot
* Tomato mosaic virus
* Leaf_Mold
* Spider mites (Two-spotted spider mite)
* Powdery Mildew

---

## Key Features
* **AI-Powered Diagnosis:** Uses an ensemble of three state-of-the-art CNN models (ResNet, MobileNet, EfficientNet) for high-accuracy disease classification.
* **Offline Capability:** Performs inference directly on the device using TensorFlow Lite, ensuring functionality in areas with poor or no internet connectivity.
* **Bilingual Support:** Interface available in both **English** and **regional languages** to break linguistic barriers for farmers.
* **Real-Time Feedback:** Instant analysis of leaf images with actionable recommendations for preventive and therapeutic treatments.
* **Optimized Performance:** Uses model quantization to reduce app size (MobileNet compressed by 75% to ~3.3 MB) without sacrificing accuracy (97.45%).
* **Quality Control:** Built-in image quality checks (blur, lighting detection) to ensure accurate analysis.

---

## Tech Stack
* **Frontend / Mobile App:** Flutter & React Native (Cross-platform support for Android & iOS)
* **Machine Learning Models:**
    * **Architectures:** ResNet, MobileNet, EfficientNet
    * **Training Strategy:** Ensemble learning with a voting mechanism
    * **Deployment:** TensorFlow Lite (for on-device inference)
* **Dataset:** PlantVillage dataset (augmented with field data)
* **Image Processing:** Resizing (224x224), Normalization, Quality assessment

---

## System Architecture
The system is organized into five distinct layers to ensure efficiency and scalability:

1.  **User Interface Layer:** Built with Flutter; handles user interaction and bilingual display.
2.  **Application Layer:** Manages application logic, user login, history logs, and session management.
3.  **Processing Layer:** Prepares images for the AI model (resizing, color normalization, noise reduction).
4.  **Inference Layer:** The core engine hosting the **Ensemble Model**. It runs input through ResNet, MobileNet, and EfficientNet in parallel and aggregates results via a voting system.
5.  **Data Layer:** Local storage for disease knowledge base, treatment recommendations, and user history (offline-first approach).

---

## How It Works
1.  **Image Capture:** The farmer opens the app and captures a photo of a diseased leaf using the in-app camera with guidance overlays.
2.  **Quality Check:** The app instantly validates the image. If it is blurry or too dark, the user is prompted to retake it.
3.  **Preprocessing:** The valid image is resized to **224x224 pixels** and color-normalized to match training conditions.
4.  **Ensemble Analysis:** The image is fed into the three CNN models. Each model predicts the disease class and confidence score.
5.  **Voting & Diagnosis:** A voting algorithm combines the predictions. If the models agree (high confidence), a final diagnosis is generated.
6.  **Recommendation:** The app displays the identified disease along with a tiered list of treatments—ranging from low-cost cultural practices to chemical interventions.
7.  **Archival:** The result is saved to the local history for future reference.

---
