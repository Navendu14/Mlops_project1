# MLOps Project - Vehicle Insurance Data Pipeline
Welcome to an enterprise-grade **MLOps Project Pipeline** that demonstrates how to take a machine learning model from **development to production** with proper structuring, modularization, and deployment.

This project highlights best practices including:

- Scalable Project Template
- Cloud Integration (MongoDB Atlas, AWS S3, EC2)
- CI/CD with GitHub Actions, Docker & Self-Hosted Runner
- Model Registry, Monitoring & Real-Time Inference API

---

## 📁 Project Setup

```bash
# 1. Scaffold the project
python template.py

# 2. Enable local package importing
#    via setup.py and pyproject.toml (refer crashcourse.txt)

# 3. Create and activate virtual environment
conda create -n vehicle python=3.10 -y
conda activate vehicle

# 4. Install dependencies
pip install -r requirements.txt

# 5. Verify installation
pip list

```
## 🌐 MongoDB Atlas Integration

- Sign up on **[MongoDB Atlas](https://www.mongodb.com/cloud/atlas)**  
- Create a **project** and **M0 cluster**  
- Setup **username**, **password**, and **IP access**: `0.0.0.0/0`  
- Get the **Python connection string**  
- Create `notebook/mongoDB_demo.ipynb` and upload your dataset  
- Push dataset to MongoDB  
- Confirm upload via **Atlas → Collections**

---

## 📊 Logging, Exceptions, and Notebooks

- Built reusable `logger.py` and `exception.py` modules  
- Tested using `demo.py`  
- EDA & Feature Engineering performed inside `notebook/`

---

## 📥 Data Ingestion

- Define constants and DB connection in:  
  - `constants/__init__.py`  
  - `configuration/mongo_db_connection.py`  

- Fetch and transform data in:  
  - `data_access/proj1_data.py`  

- Set environment variable:
```bash
export MONGODB_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net"
```
---

### ✅ Data Validation & Transformation

- Schema defined in `config/schema.yaml`  
- Utilities added in `utils/main_utils.py`

**Components:**
- `data_validation.py`
- `data_transformation.py`

---

### 🧠 Model Training & Evaluation

- Scikit-learn-based pipelines created for training
- Evaluation with drift detection threshold:

```python
MODEL_EVALUATION_CHANGED_THRESHOLD_SCORE = 0.02
```

---

### ☁️ AWS S3 & Model Registry

#### IAM & Bucket Setup

1. Create an **IAM user** with `AdministratorAccess`  
2. Generate **Access Keys** and set environment variables:

```bash
export AWS_ACCESS_KEY_ID="..."
export AWS_SECRET_ACCESS_KEY="..."
```

3. Create S3 bucket: `my-model-mlopsproj`  
   - Region: `us-east-1`

#### Configuration Added In:

- `configuration/aws_connection.py`
- `aws_storage/`
- `entity/s3_estimator.py`

---

### 📦 CI/CD with Docker, GitHub Actions & EC2

#### 🐳 Docker & GitHub Workflow

Create the following files:

- `Dockerfile`
- `.dockerignore`
- `.github/workflows/aws.yaml`

#### ⚙️ AWS Setup

1. Create IAM user: `usvisa-user`  
2. Create ECR repo: `vehicleproj`  
3. Launch EC2 instance (Ubuntu, T2 Medium)

Install Docker:

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

#### 🏃 Self-Hosted Runner

- Go to GitHub → **Settings > Actions > Runners**  
- Follow setup instructions on your EC2 instance

#### 🔐 GitHub Secrets

Set the following under **Settings > Secrets > Actions**:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_DEFAULT_REGION`
- `ECR_REPO`

---

### 📲 Prediction API (Flask)

- Web UI built using **Flask**

**Routes:**
- `/` → Inference Page  
- `/training` → Triggers pipeline

**Folder Structure:**

```plaintext
📂 templates/
📂 static/
📜 app.py
```

---

### 📸 Final Deployment

1. Go to **EC2 → Security → Inbound Rules**
2. Add new rule:  
   - **Port**: `5080`  
   - **Source**: `0.0.0.0/0`

3. Launch App:

```bash
http://<EC2-Public-IP>:5080
```

---

### 📚 Learnings & Takeaways

✅ Learned and implemented:

- Modular Python Package Development  
- MongoDB Atlas & NoSQL Integration  
- Scalable ML Pipeline Architecture  
- Docker + GitHub Actions for CI/CD  
- AWS S3, ECR, EC2 Automation  
- Secure Model Registry + Real-time API  

---

### 🤝 Connect With Me

📧 navendupandey14@gmail.com
🔗 www.linkedin.com/in/navendu-pandey-a11a06352



