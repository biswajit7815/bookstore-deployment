# 📚 MERN Bookstore Application

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![NodeJS](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)

> Full-stack MERN Bookstore containerized with production level Dockerfile and docker-compose.yml, deployed on AWS EC2

🌐 **Live Demo:** [http://13.205.178.68](http://13.205.178.68)


## 🏗️ Architecture
```
Internet
    ↓
AWS EC2 (Ubuntu) - Elastic IP: 13.205.178.68
    ↓
┌─────────────────────────────────┐
│  Nginx (Port 80)                │
│  ├── / → React Frontend        │
│  └── /api/* → Backend:5000     │
│                  ↓              │
│             MongoDB:27017       │
└─────────────────────────────────┘
```

---

## 🐳 Docker Services
```
mern-bookstore/
├── 🍃 mongodb        → Database + Persistent Volume
├── 🟢 backend        → Node.js API (Port 5000)
├── ⚛️  frontend-build → Vite Build Container
└── 🔀 nginx          → Reverse Proxy (Port 80)
```

---

## ✨ Features

| Feature | Status |
|---------|--------|
| 📚 Browse Books by Category | ✅ |
| 🛒 Add to Cart | ✅ |
| 🔐 Google OAuth Login | ✅ |
| 👤 User Order Dashboard | ✅ |
| 🔑 Admin Panel | ✅ |
| 📱 Responsive Design | ✅ |
| 🐳 Dockerized | ✅ |
| ☁️ AWS EC2 Deployed | ✅ |

---

## 🚀 Quick Start
```bash
# Clone karo
https://github.com/biswajit7815/bookstore-deployment.git
cd booksstore-deployment

# Environment setup
cp .env.example .env
# .env me apni values dalo

# Deploy!
docker-compose up -d --build
```

---

## 📁 Project Structure
```
mern-bookstore/
├── 📁 backend/
│   ├── 📁 src/
│   │   ├── books/
│   │   ├── orders/
│   │   ├── users/
│   │   └── stats/
│   ├── Dockerfile
│   └── .env
├── 📁 frontend/
│   ├── 📁 src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── redux/
│   │   └── utils/
│   ├── Dockerfile
│   └── .env
├── 📁 nginx/
│   └── nginx.conf
├── 📁 images/          ← Screenshots
├── docker-compose.yml
└── README.md
```

---

## 🔧 Environment Variables

**Root `.env`**
```env
MONGO_USER=your_username
MONGO_PASS=your_password
VITE_API_KEY=firebase_api_key
VITE_Auth_Domain=project.firebaseapp.com
VITE_PROJECT_ID=project_id
VITE_STORAGE_BUCKET=project.appspot.com
VITE_MESSAGING_SENDERID=sender_id
VITE_APPID=app_id
```

**`backend/.env`**
```env
DB_URL=mongodb://user:pass@mongodb_services:27017/bookdb?authSource=admin
PORT=5000
JWT_SECRET_KEY=your_secret_key
```

---

## 🐛 Issues I Solved

| Problem | Solution |
|---------|----------|
| Vite env vars in Docker | Used `build args` instead of `env_file` |
| Nginx wrong routing | Added `/api/` in `proxy_pass` |
| Firebase unauthorized domain | Added EC2 IP to Firebase Console |
| CORS error | Added EC2 IP to backend CORS origin |
| Images not loading | Updated `getImgUrl()` for external URLs |
| JWT secret missing | Fixed `.env` file in Docker build |
| IP changing on restart | AWS Elastic IP allocated |

---

## 📊 Useful Commands
```bash
# Containers check karo
docker-compose ps

# Logs dekho
docker-compose logs -f backend

# Restart karo
docker-compose restart nginx

# Full rebuild
docker-compose down && docker-compose up -d --build

# MongoDB connect
docker exec -it mongodb_services mongosh -u admin -p pass --authenticationDatabase admin
```

---

## 🔜 What's Next

- [ ] 🔒 HTTPS with Let's Encrypt SSL
- [ ] 🔄 CI/CD with GitHub Actions
- [ ] 📊 Monitoring with Prometheus & Grafana
- [ ] ☸️ Kubernetes Deployment
- [ ] 📦 AWS S3 for Image Storage

---

## 👨‍💻 Author

**Biswajit Behera**
*DevOps Engineer*

[![LinkedIn](www.linkedin.com/in/biswajit-behera-1b564031a)

---

⭐ **Star this repo if you found it helpful!** ⭐
