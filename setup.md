# Setup Guide: End-to-End Deep Learning Pipeline with MLOps Tools

This guide walks you through the setup process of the **End-to-End Deep Learning Pipeline** using MLOps tools like **MLflow**, **DVC**, and **CI/CD** practices for production-grade deep learning applications. You can use this template with minimal changes for various deep learning use cases. Follow the steps below to configure the pipeline for your project.

## Prerequisites

1. **Python 3.8** installed
2. **AWS Account** for deployment (optional)
3. **GitHub** account for version control and CI/CD setup
4. **Docker** installed for containerization
5. **DVC** and **MLflow** installed for experiment tracking and versioning

### Key MLOps Tools

- **MLflow**: Tracks experiments, logs models, and stores results for production tracking.
- **DVC**: Manages datasets, models, and pipelines efficiently with version control.

---

## 1. Project Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/your-username/deep-learning-pipeline.git
   cd deep-learning-pipeline
   ```

2. **Install Dependencies**

   Install all required packages using the provided `requirements.txt` file:

   ```bash
   pip install -r requirements.txt
   ```

3. **Initialize DVC**

   Initialize DVC to manage datasets and pipelines:

   ```bash
   dvc init
   ```

---

## 2. Update Configuration Files

This template is highly customizable. Here’s a list of files you can update to adapt the pipeline for your specific deep learning use case:

### 1. **`config.yaml`**

   Modify `config.yaml` to set the configurations for data paths, model hyperparameters, etc. These settings will be used across the pipeline.

### 2. **`params.yaml`**

   Adjust `params.yaml` to reflect new parameters for your model and experiments. This includes learning rates, optimizer settings, etc.


### 3. **`secrets.yaml`** [Optional]

   Use this file to store sensitive data, such as API keys and authentication tokens.


### 4. **Entity and Configuration Manager**

   Update the **entity** and **configuration manager** under the `src/config` folder to match your specific data structure and model requirements.


### 5. **Pipeline & Components**

   Update the core **pipeline** logic and relevant **components** to fit your deep learning task, such as image classification, NLP, or any other domain. Customize model architectures, preprocessing steps, or evaluation metrics.

   - Modify data loaders in `data_ingestion.py`.
   - Customize model architecture in `model.py`.
   - Update evaluation metrics in `evaluation.py`.

### 6. **Update DVC Pipelines**

   Update `dvc.yaml` to define new stages and pipelines for your project. For example, if you’re adding a new preprocessing step or evaluation, it should be reflected here.

   ```yaml
   stages:
     preprocess:
       cmd: python src/data_preprocessing.py
       deps:
         - src/data_preprocessing.py
       outs:
         - data/processed
   ```

---

## 3. Experiment Tracking with MLflow

### Starting MLflow UI

MLflow allows you to track all experiments and compare model performance. Run the following command to start the MLflow UI locally:

```bash
mlflow ui
```

Access the dashboard at `http://127.0.0.1:5000`.

### DagsHub Integration

You can also track experiments on **DagsHub** by exporting the necessary environment variables:

```bash
export MLFLOW_TRACKING_URI=https://dagshub.com/your-username/project-name.mlflow
export MLFLOW_TRACKING_USERNAME=your-username
export MLFLOW_TRACKING_PASSWORD=your-password
```

Now, run your scripts as usual, and the results will be logged on **DagsHub**:

```bash
python src/train.py
```

---

## 4. Managing Pipelines with DVC

DVC is used for pipeline orchestration and managing data/model versions. Use the following commands to run the pipeline and view the stages:

### Initialize DVC

```bash
dvc init
```

### Track Data and Models

```bash
dvc repro
```

### View Pipeline Structure

```bash
dvc dag
```

This command will display the pipeline stages and dependencies.

---

## 5. Deployment on AWS with CI/CD

This project comes with a **CI/CD pipeline** using **GitHub Actions** for automated testing and deployment.

### 1. AWS Setup

- Create an **IAM user** with permissions for **EC2** and **ECR** (Elastic Container Registry).
- Create an **ECR repository** to store Docker images for the project.
- Create an **EC2** instance to serve as the host for the model.

### 2. Dockerize Your Application

- Build a Docker image of your application:

   ```bash
   docker build -t cancer-classifier .
   ```

- Push the image to your ECR repository:

   ```bash
   aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 566373416292.dkr.ecr.us-east-1.amazonaws.com
   docker tag cancer-classifier:latest 566373416292.dkr.ecr.us-east-1.amazonaws.com/cancer-classifier:latest
   docker push 566373416292.dkr.ecr.us-east-1.amazonaws.com/cancer-classifier:latest
   ```

### 3. CI/CD Pipeline Setup

The **GitHub Actions** workflow automates deployment. Update your secrets in the GitHub repository settings:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_REGION`
- `AWS_ECR_LOGIN_URI`
- `ECR_REPOSITORY_NAME`

Upon each push, GitHub Actions will automatically build and deploy your Docker image to AWS EC2 using the self-hosted runner.

---

## 6. Customizing for Other Use Cases

This template can be adapted for various deep learning tasks with minimal changes:
- **For NLP**: Modify the model architecture to include RNNs or transformers.
- **For Object Detection**: Integrate object detection frameworks like YOLO or Faster R-CNN.
- **For Time Series**: Adapt the pipeline for sequence models (LSTMs, GRUs) and modify data ingestion to handle sequential data.

Simply update the configuration files, model architecture, and data processing scripts to match the requirements of your project.

---

## Conclusion

This project serves as a template for production-grade deep learning pipelines with **MLOps tools** like MLflow, DVC, and AWS. With slight modifications to the configuration and components, you can use this structure for any advanced deep learning use case. Happy coding!

