# Technical Deep Dive: CuraMatch-AI Resilience Engine

This project demonstrates my proficiency in building a secure, full-stack, single-page web application with a focus on real-time data persistence and AI integration.

## 🎯 My Role and Technical Challenges
My primary goal was to create a reliable assessment tool that not only scored the user but also provided customized, insightful guidance—moving beyond static recommendations.

### 1. Secure and Real-time Data Persistence
* **Skill Demonstrated:** Full-stack architecture, Firebase integration, asynchronous programming.
* **Implementation:** I utilized the Firebase JavaScript SDK to initialize the application and authenticate the user using the securely provided `__initial_auth_token`. All assessment records are stored in Firestore using the private path `/artifacts/{appId}/users/{userId}/history`, ensuring data segmentation and privacy.
* **Challenge & Solution:** The main challenge was ensuring data was retrieved and updated in real-time without excessive load. I implemented **`onSnapshot()`** listeners for the user's history collection, allowing the 'History' tab to update instantly whenever a new assessment was saved, resulting in a smooth, dynamic user experience.

### 2. LLM Integration for Personalized Feedback
* **Skill Demonstrated:** API integration, prompt engineering, asynchronous error handling.
* **Implementation:** The core of the recommendation engine relies on a `fetch` request to the **Gemini API** (`gemini-2.5-flash-preview-09-2025`). The user's scores are sent as part of the prompt, along with a System Instruction, tasking the model to act as a "well-being coach" and provide a concise, tailored summary.
* **Challenge & Solution:** I implemented an exponential backoff retry mechanism for the API calls to handle potential network throttling and rate-limiting robustly, ensuring that a recommendation is always generated and displayed, or a clear error message is logged to the console.

### 3. Maintainable Single-File Architecture
* **Skill Demonstrated:** Front-end development, responsive design, component isolation.
* **Implementation:** The entire application (HTML, Tailwind CSS for aesthetics, and JavaScript for logic) is contained within a single file. This demonstrates mastery of organizing complex code, separating concerns effectively within a monolithic structure, and using component-based thinking (even in vanilla JS) to manage the UI. The use of Tailwind ensures full responsiveness across all major device breakpoints.