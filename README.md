# WildlifeGuard: AI-Powered Anti-Poaching & Animal Detection System
> A real-time intelligent surveillance system designed to protect endangered species through automated detection and instant remote alerting.

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![YOLOv8](https://img.shields.io/badge/Object_Detection-YOLOv8-red.svg)](https://ultralytics.com/)
[![Streamlit](https://img.shields.io/badge/UI-Streamlit-FF4B4B.svg)](https://streamlit.io/)
[![Status](https://img.shields.io/badge/Status-Prototype_Complete-success.svg)]()

## 📌 Overview
Poaching remains a critical threat to global biodiversity. **WildlifeGuard** leverages state-of-the-art Computer Vision to provide a 24/7 monitoring solution. The system identifies over 90 species of animals in real-time and immediately dispatches email alerts to conservation authorities upon detection, bridging the gap between surveillance and rapid response.

## ✨ Key Features
* **Multi-Modal Detection:** Supports static images, recorded video files, and live webcam/CCTV streams.
* **High-Precision AI:** Powered by a custom-trained **YOLOv8** model capable of identifying 90+ distinct animal classes.
* **Automated Alerting:** Integrated **SMTP protocol** to send instant email notifications with the specific animal species detected.
* **Secure Infrastructure:** Features a robust user authentication system using **SQLite3** and **PBKDF2 password hashing** for secure ranger/admin access.



## 🛠️ Tech Stack
* **Model:** YOLOv8 (Ultralytics)
* **Frontend:** Streamlit
* **Backend/Database:** Python, SQLite3
* **Security:** Passlib (PBKDF2-SHA256)
* **Image Processing:** OpenCV, CVZone

## 📊 Class Coverage
The system is trained to recognize a vast array of wildlife, including:
`Antelope, Bison, Cheetah, Elephant, Lion, Leopard, Rhinoceros, Tiger, Zebra, and many more (90+ total classes).`

## 🚀 Installation & Usage
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/WildlifeGuard.git](https://github.com/yourusername/WildlifeGuard.git)
   cd WildlifeGuard
