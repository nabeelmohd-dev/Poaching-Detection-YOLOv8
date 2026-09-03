# WildlifeGuard: AI-Powered Anti-Poaching & Animal Detection System
> A real-time intelligent surveillance system designed to protect endangered species through automated detection and instant remote alerting.

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![YOLOv8](https://img.shields.io/badge/Object_Detection-YOLOv8-red.svg)](https://ultralytics.com/)
[![Streamlit](https://img.shields.io/badge/UI-Streamlit-FF4B4B.svg)](https://streamlit.io/)
[![Status](https://img.shields.io/badge/Status-Prototype_Complete-success.svg)]()

## 📌 Overview

Poaching remains a critical threat to global biodiversity. **WildlifeGuard** leverages state-of-the-art computer vision to provide a 24/7 monitoring solution. The system identifies over 90 species of animals in real-time and immediately dispatches email alerts to conservation authorities upon detection, bridging the gap between surveillance and rapid response.

## ✨ Key Features

* **Multi-Modal Detection:** Supports static images, recorded video files, and live webcam/CCTV streams.
* **High-Precision AI:** Powered by a custom-trained **YOLOv8** model (`main.pt`) capable of identifying 90+ distinct animal classes.
* **Automated Alerting:** Integrated **SMTP protocol** to send instant email notifications with the specific animal species detected.
* **Secure Infrastructure:** User authentication backed by **SQLite3**, with passwords stored using **PBKDF2-SHA256** hashing (via `passlib`) rather than in plain text.

## 🛠️ Tech Stack

* **Model:** YOLOv8 (Ultralytics)
* **Frontend:** Streamlit
* **Backend/Database:** Python, SQLite3
* **Security:** Passlib (PBKDF2-SHA256), python-dotenv
* **Image Processing:** OpenCV, CVZone

## 📊 Class Coverage

The system is trained to recognize a wide range of wildlife, including:

`Antelope, Bison, Cheetah, Elephant, Lion, Leopard, Rhinoceros, Tiger, Zebra, and many more (91 total classes).`

## 🚀 Installation & Usage

### Prerequisites

* Python 3.9 or higher
* Trained YOLOv8 weights file, `main.pt`, placed in the project root
* A Gmail (or other SMTP) account with an **app password** for sending alerts, see the security note below before doing anything else

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/WildlifeGuard.git
cd WildlifeGuard
```

### 2. Set up a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install streamlit ultralytics opencv-python cvzone numpy passlib python-dotenv
```

Or, if you maintain a `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 4. Configure email alerts ⚠️ required security step

The alerting code currently expects an SMTP login and a recipient address. **Do not hardcode these values in the source file.** Create a `.env` file in the project root instead:

```env
SMTP_SERVER=smtp.gmail.com
SMTP_PORT=587
SENDER_EMAIL=your_email@example.com
SENDER_PASSWORD=your_gmail_app_password
ALERT_RECIPIENT=ranger_or_authority@example.com
```

Then load these with `os.getenv(...)` (via the `python-dotenv` import already in the app) instead of passing literal strings to `smtplib`. Add `.env` to `.gitignore` so it is never committed.

> **If credentials were ever hardcoded and pushed to a repo, rotate that app password immediately in your Google Account's App Passwords settings, even after removing it from the code** it remains recoverable from git history otherwise.

### 5. Run the app

```bash
streamlit run app.py
```

The app opens in your browser. Sign up for a ranger/admin account (or log in if you already have one), then choose an input type (image, video, or webcam) to start detection. Any detected animal above the confidence threshold triggers an email alert to the configured recipient.

## 🔒 Security Notes

* Passwords are hashed with PBKDF2-SHA256 before being stored in SQLite, never stored or compared in plain text.
* SMTP credentials must be supplied via environment variables (see step 4), not hardcoded.
* The SQLite database file (`user_database.db`) and any `.env` file should be excluded from version control via `.gitignore`.

## 📜 License

Distributed under the MIT License. See `LICENSE` for details.

## ⚠️ Disclaimer

This project is a prototype developed for educational and demonstration purposes. Detection accuracy is not guaranteed, and it should not be relied upon as a sole safeguard for anti-poaching operations without further testing, validation, and integration with existing conservation infrastructure.
