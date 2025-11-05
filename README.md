Smart Grading Engine

AI-Powered Automatic Grading System for Teachers
Built using Flask • Mistral AI OCR • SQLAlchemy • Chart.js

📋 Overview

Smart Grading Engine is an intelligent AI tool that automatically evaluates handwritten or digital student answers.
It extracts text from answer sheet images using Mistral AI OCR, compares it to the teacher’s reference answer, and instantly provides:
✅ Grade (A–F)
✅ Marks (%)
✅ Similarity Score
✅ Highlighted matched and missing keywords

It also includes a dashboard to track student performance, grade distribution, and class progress — making grading fast, transparent, and smart.

🚀 Features

🧾 Automatic AI Grading — instantly grade handwritten or typed answers

🤖 OCR Integration — extracts text using Mistral AI OCR

📊 Analytics Dashboard — visualizes grades, averages, and trends

📥 CSV Export — download all grading data

💾 Persistent Storage — stores all graded results in SQLite

⚡ Simple UI — built with Flask & Bootstrap

🔒 Secure API Key Handling — environment variable for Mistral API

🧩 Tech Stack
Layer	Technology
Frontend	HTML5, CSS3, Bootstrap 5, Chart.js
Backend	Flask (Python)
AI OCR	Mistral AI
Database	SQLite (via SQLAlchemy ORM)
Deployment	Railway / Render / Replit
🧠 How It Works

Teacher uploads a student’s answer image or pastes the text.

Mistral AI OCR extracts text from the image.

The app compares extracted text with the teacher’s correct answer.

Grades and marks are assigned based on keyword similarity.

All results are saved and displayed in a dashboard with visual analytics.

⚙️ Project Structure
Smart-Grading-Engine/
├── app.py               # Flask app with routes and grading logic
├── models.py            # SQLAlchemy model for storing results
├── requirements.txt     # Dependencies
├── runtime.txt          # Python version (for Render/Railway)
├── templates/
│   ├── index.html       # Upload and grading form
│   ├── result.html      # Display grading results
│   └── dashboard.html   # Analytics dashboard
├── uploads/             # Stores uploaded student images
└── smart_grading.db     # SQLite database (auto-created)

🧪 Installation & Setup
1️⃣ Clone the Repository
git clone https://github.com/Tripathi-Nishant/Smart-Grading-Engine.git
cd Smart-Grading-Engine

2️⃣ Create a Virtual Environment
python -m venv venv
venv\Scripts\activate   # Windows
source venv/bin/activate   # macOS/Linux

3️⃣ Install Dependencies
pip install -r requirements.txt

4️⃣ Add Mistral API Key

Set your Mistral API key securely:

🪟 Windows
set MISTRAL_API_KEY=your_api_key_here

🍎 macOS/Linux
export MISTRAL_API_KEY=your_api_key_here

5️⃣ Run the App
python app.py


Now open 👉 http://127.0.0.1:5000

📊 Analytics Dashboard

The built-in dashboard provides:

🥧 Grade Distribution
📈 Average Marks by Student
📅 Performance Trend Over Time
📤 CSV Export of Results
👨‍💻 Developer
