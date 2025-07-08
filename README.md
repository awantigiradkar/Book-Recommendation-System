# Book-Recommendation-System
An end-to-end book recommendation system using collaborative filtering with a simple, interactive UI built in Streamlit. It recommends books based on user input and displays book covers, titles, and authors. You can run it locally, on Streamlit Cloud, or deploy it using **Docker on AWS EC2**.

🔗 **Live Demo**: [https://bookrecommendationsys.streamlit.app](https://bookrecommendationsys.streamlit.app)

---

## Features

- Search a Book and get 4 similar recommendations.
- Collaborative Filtering using cosine similarity.
- Precomputed similarity for fast results.
- Book Metadata Display (cover, author, title).
- Deployable on AWS EC2 using Docker.
- Runs on Streamlit Cloud or locally.

---

## 🛠️ Tech Stack

| Layer        | Tool / Library             |
|--------------|-----------------------------|
| Language     | Python                      |
| Frontend     | Streamlit                   |
| Backend      | Precomputed similarity (cosine) |
| Data         | Book metadata + similarity matrix |
| Deployment   | Streamlit Cloud, Docker, AWS EC2 |

---

## Project Structure
Book-Recommendation-System/
│
├── app.py # Streamlit frontend
├── main.py # Entry script
├── components/ # Core logic
├── config.yaml # Configuration file
├── config/
│ └── configuration.py # Config loader
├── entity/ # Data classes
├── pipeline/ # Data pipelines
├── similarity.pkl # Cosine similarity matrix
├── book_dict.pkl # Book metadata dictionary
├── requirements.txt # Project dependencies
└── README.md

---

## Setup Instructions (Local)

### Clone the Repository

```bash
git clone https://github.com/awantigiradkar/Book-Recommendation-System.git
cd Book-Recommendation-System
```
### Create a Virtual Environment
```bash
python -m venv venv
venv\Scripts\activate
```

### Install Dependencies
``` bash
pip install -r requirements.txt
```
### Run the App
```bash
streamlit run app.py
```
# Docker Deployment on AWS EC2
Step-by-Step Guide
Make sure to allow inbound traffic on port 8501 in your AWS EC2 security group.

### 1. Launch an EC2 Instance
Choose an Ubuntu image (e.g., Ubuntu 20.04)
Set up key pair, security group, and login

### 2. SSH into EC2 and Install Docker
``` bash
sudo apt-get update -y
sudo apt-get upgrade -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

### 3. Clone the Repository
```bash
git clone https://github.com/awantigiradkar/Book-Recommendation-System.git
cd Book-Recommendation-System
```
### 4. Build Docker Image
```bash
docker build -t book-recommender-app:latest .
```
### 5. Run the Container
```bash
docker run -d -p 8501:8501 book-recommender-app
```
Now, open http://<your-ec2-public-ip>:8501 in your browser to access the app.

### Docker Cleanup Commands
```bash
docker ps                         # View running containers
docker stop <container_id>        # Stop container
docker rm $(docker ps -a -q)      # Remove all containers
docker rmi book-recommender-app   # Remove image
```

