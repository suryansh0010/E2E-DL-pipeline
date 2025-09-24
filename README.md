# End-to-End Deep Learning Pipeline with MLOps: Cancer Classification using CT Scans 🚀

This repository showcases an **end-to-end deep learning project** implementation focused on **chest cancer classification** using CT scan images. We leverage **MLOps tools** like **MLflow** and **DVC (Data Version Control)** for robust experiment tracking, data versioning, and model management, alongside **CI/CD** pipelines for seamless deployment to **AWS**. The pipeline spans from **data ingestion** to **production deployment**, covering all critical stages of the machine learning lifecycle, including model evaluation and deployment.

![image](https://github.com/user-attachments/assets/9f39fecb-9d0e-4f12-b34f-8c926fac48a8)

## 🌟 Key Features

### 1. **Project Structure & Setup**
   - A well-structured project layout with modularized codebase.
   - Programmatic template creation to standardize components for **data ingestion**, **model training**, and **evaluation**.
   - Configurable architecture for seamless scaling.

### 2. **Data Ingestion Pipeline**
   - Automated pipeline to ingest CT scan image datasets.
   - Data preprocessing steps include handling missing values, augmentations, and data normalization.
   - Source data is retrieved from Google Drive, with detailed metadata tracking using **DVC**.

### 3. **Base Model & Custom Model Training**
   - Initial base model training followed by enhanced **CNN architecture** for image classification.
   - Use of **TensorFlow** for model building, with MLflow logging for every experiment.
   - **Hyperparameter tuning** to find the best configuration using **grid search** and **random search**.

### 4. **Experiment Tracking & Management**
   - Integrated with **MLflow** for tracking model parameters, metrics, and artifacts.
   - **DagsHub** as a collaborative platform for visualizing experiments and sharing results with the team.
   - Comparison of multiple experiment runs to select the best-performing model.
     ![image](https://github.com/user-attachments/assets/3d83e025-2080-4bdf-819f-0eac46a63940)


### 5. **Pipeline Tracking with DVC**
   - Complete versioning of datasets, model checkpoints, and pipelines using **DVC**.
   - Allows efficient collaboration and ensures reproducibility across environments.
   - Streamlined processes to handle large datasets without manual tracking.

### 6. **Evaluation & Model Comparison**
   - Multiple metrics logged for every model run (accuracy, F1-score, AUC, etc.).
   - Visualizations to compare different experiments and their outcomes.
   - Cross-validation results help in selecting the best model architecture for production.

### 7. **CI/CD Pipeline using GitHub Actions**
   - **GitHub Actions** set up for continuous integration, automating testing, training, and deployment workflows.
   - Automated testing for every code commit, ensuring high-quality code and preventing regressions.
   - Seamless push-to-production flow, reducing manual intervention and speeding up the deployment process.

### 8. **Deployment to AWS**
   - Dockerized deployment using **Docker containers**.
   - Model served through **AWS Elastic Beanstalk**, providing scalable and efficient cloud hosting.
   - Secure deployment using **CI/CD pipelines**, ensuring fast iteration cycles.

### 9. **User Interface for Predictions**
   - A **Flask-based web application** to allow users to upload CT scan images and receive predictions in real-time.
   - Deployed model integrated into the web app, providing seamless access to the trained classifier.
   - Simplified and user-friendly interface for non-technical users.

---

## 🛠 Tools & Technologies

- **TensorFlow**: Deep Learning framework for model building.
- **MLflow**: Experiment tracking and model management.
- **DVC**: Data versioning and pipeline tracking.
- **GitHub Actions**: CI/CD pipeline automation.
- **AWS Elastic Beanstalk**: Cloud deployment platform.
- **Docker**: Containerization for consistent deployment.
- **Flask**: Web framework for user interface.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check out the [issues page](https://github.com/your-username/deep-learning-pipeline/issues).

