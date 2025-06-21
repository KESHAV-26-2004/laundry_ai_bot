# 🧠 Laundry AI Bot — FLAN-T5 Based Chat Assistant

This repository contains the AI backend for our **Laundry Management App**, built using **Python**, **Flask**, and a **custom-trained FLAN-T5 model**. The chatbot answers user queries related to laundry services, such as pricing, service types, delays, refund status, order progress, and more.

---

## 🤖 Features

- ✅ Trained on 500+ real FAQ & dialogue samples
- 🧠 Uses FLAN-T5 (via HuggingFace Transformers)
- 🌐 REST API powered by Flask
- 🔌 Flutter integration-ready (via `connect.dart`)
- 📝 Easy-to-extend with new questions
- 💬 Natural language understanding of laundry queries

---

## 📁 Project Structure
``` bash
Laundry_ai_bot/
├── Datasets/
│ ├── laundry_dataset.json
│ ├── laundry_faq_500_basic.json
│ └── general_question.ipynb
├── connector/
│ └── connect.dart # Flutter → API connection
├── MODEL_FLAN_T5_BASE.ipynb # Model training notebook
├── CONNECTOR.ipynb # Chat API testing in Colab
├── flask_app.py # Flask server with POST endpoint
├── requirements.txt
└── README.md
```

---

## 🧠 Model Details

- Architecture: `FLAN-T5 Base`
- Trained in Colab using PyTorch
- File: `flan_laundry_bot1_8_lr5e-05.pth` (tracked via Git LFS)
- Input: JSON-based prompt → Output: Answer string

---

## 🔌 How to Use the API

1. Install Dependencies
```bash
pip install -r requirements.txt
```

2. Run the Flask API
```bash
python flask_app.py
```
It will run at: http://localhost:5000/get-response

3. Example API Call (from Flutter)
```bash
final response = await http.post(
  Uri.parse('http://localhost:5000/get-response'),
  headers: {"Content-Type": "application/json"},
  body: jsonEncode({"query": userQuestion}),
);
```
---

🌐 Public Access via ngrok
To connect this local API with the Flutter app, we used ngrok to expose the Flask server to the internet.

Steps:
```bash
ngrok http 5000
This will give you a public URL like:
```

```arduino
https://abc1234.ngrok.io
Use this in your Flutter app inside connect.dart:
```

```dart
Uri.parse("https://abc1234.ngrok.io/get-response");
```
⚠️ Note: ngrok URLs change every time unless you have a paid plan with a reserved domain.

---

📎 Related Repo

👉 Laundry App GitHub:
https://github.com/KESHAV-26-2004/laundry-app

---

👨‍💻 Developed By

Keshav Verma
Bennett University | BTech CSE

---

📜 License

This project and model are trained entirely by me.

You’re welcome to learn from or extend it, but please don't redistribute the model without permission.
