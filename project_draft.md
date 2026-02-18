# Kidney Tumor Identification System - Project Draft

## 1. Project Overview
The **Kidney Tumor Identification System** is a state-of-the-art Deep Learning application designed to assist medical professionals in the early detection and classification of kidney tumors from CT scan images. By leveraging Convolutional Neural Networks (CNNs) and MLOps best practices, this system provides accurate, automated diagnostics to reduce the workload on radiologists and improve patient outcomes.

### Core Problems Solved
*   **Manual Diagnosis Fatigue**: Reduces human error associated with reviewing thousands of CT scans.
*   **Speed & Scalability**: Provides instant analysis results, scalable via cloud deployment.
*   **Standardization**: Ensures consistent classification criteria across different medical facilities.

## 2. System Architecture
The project follows a modular pipeline architecture, ensuring reproducibility and scalability.

### High-Level Components
1.  **Data Ingestion**: Automated download and extraction of CT scan datasets.
2.  **Data Validation**: Integrity checks to ensure input data meets training requirements.
3.  **Model Training (DVC)**:
    *   **Base Model**: Utilizes VGG16 (or similar) pre-trained on ImageNet.
    *   **Training**: Fine-tuning the model on the specific kidney dataset.
    *   **Evaluation**: Metrics generation (Accuracy, Loss) tracked via MLflow.
4.  **Web Serving**: A Flask-based REST API serves the model for real-time predictions.
5.  **CI/CD & Deployment**:
    *   **GitHub Actions**: Orchestrates build and deploy steps.
    *   **Docker**: Containerizes the application for consistency.
    *   **AWS ECR**: Stores the robust Docker images.
    *   **AWS EC2**: Hosts the running application for end-users.

## 3. Technical Stack
*   **Language**: Python 3.8+
*   **Deep Learning**: TensorFlow, Keras
*   **Web Framework**: Flask, HTML/CSS
*   **Data & MLOps**: DVC (Data Version Control), MLflow, Pandas, NumPy
*   **Infrastructure**: Docker, AWS (EC2, ECR), GitHub Actions

## 4. Key Features
*   **End-to-End Pipeline**: Fully scriptable training and inference process.
*   **Reproducibility**: DVC ensures every data version and model experiment is tracked.
*   **Experiment Tracking**: MLflow integration allows for comparing different model hyperparameters.
*   **Cloud Native**: Built to run in containers on the cloud, leveraging AWS services.
*   **User-Friendly UI**: Simple web interface for uploading CT scans and viewing results.

## 5. Deployment Guide (Summary)
1.  **AWS Setup**: Create IAM user with ECR/EC2 access.
2.  **Infrastructure**: Provision an EC2 instance and an ECR repository.
3.  **Secrets**: Configure GitHub Secrets (AWS Credentials, ECR URI).
4.  **Automation**: Push to `main` branch triggers the CI/CD pipeline, building the image and deploying to EC2.

## 6. Future Enhancements
*   **Advanced Models**: Experiment with ResNet50, InceptionV3, or Vision Transformers.
*   **Explainability**: Integrate Grad-CAM to visualize tumor regions on the CT scan.
*   **Mobile App**: Develop a mobile-friendly frontend for remote access by doctors.
*   **Multi-Class Classification**: Expand to identify specific tumor types (e.g., Angiomyolipoma vs. Renal Cell Carcinoma).
