# CuraMatch-AI Resilience Engine

## 🚀 Project Overview
The CuraMatch-AI Resilience Engine is a secure, real-time web application built for personal development and well-being tracking. It uses a structured assessment to calculate an **Overall Resilience Score** across five key domains: Emotional, Social, Professional, Adaptability, and Vision. The application provides immediate, AI-driven recommendations based on the user's results, and securely persists history and scores using Google's **Firestore** database.

## ✨ Key Features
* **Real-time Assessment:** Interactive and dynamic scoring of 20+ resilience factors.
* **AI-Driven Recommendations:** Utilizes the Gemini API to analyze the score and instantly generate a personalized, single-paragraph recommendation for improvement.
* **Secure History Tracking:** Implements **Firebase Firestore** for persistent, real-time storage of assessment history and scores, utilizing the `__initial_auth_token` for secure user authentication.
* **Single-File Architecture:** Deployed as a self-contained, fully responsive HTML file, integrating all CSS (Tailwind), JavaScript, and data logic for efficient deployment.
* **Responsive Design:** Optimized for seamless usage across mobile, tablet, and desktop devices.

## 🛠 Technology Stack
* **Frontend:** HTML5, Tailwind CSS, Vanilla JavaScript (ES6+)
* **Database:** Google Firebase Firestore
* **Authentication:** Firebase Auth (`signInWithCustomToken`)
* **AI/LLM:** Gemini API (`gemini-2.5-flash-preview-09-2025`) for content generation

## ☁️ Database Structure (Firestore)
The application uses the following secure collection path to store user history:

| Collection Path | Data Stored | Access Level |
| :--- | :--- | :--- |
| `/artifacts/{appId}/users/{userId}/history` | Assessment results (score, date, raw inputs, recommendation text) | Private (User-specific) |

## ⚙️ Installation and Setup
This application is designed to run in a secure sandbox environment where the following global variables are injected: `__app_id`, `__firebase_config`, and `__initial_auth_token`.

1.  **Clone the Repository:** `git clone [Your Repository URL]`
2.  **Deployment:** Deploy to an environment that supports dynamic injection of Firebase credentials for full database functionality. The application defaults to anonymous sign-in if the custom token is unavailable.