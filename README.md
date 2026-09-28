# 🏋️ FitBuddy – AI Fitness Plan Generator Using Gemini

FitBuddy is an AI-powered fitness planning web application that generates personalized workout plans based on a user's fitness profile, goals, body information, and preferred workout intensity.

The application uses **Google Gemini AI** to create customized workout plans and provide nutrition tips. It also stores user information and generated plans using a database.

## 🎯 Project Objective

The main objective of FitBuddy is to make fitness planning easier by providing an AI-generated workout plan instead of requiring users to manually create one.

### Main Goals
- Collect basic fitness information from the user.
- Generate a personalized workout plan using AI.
- Store user details and workout plans.
- Allow users to provide feedback and revise the generated plan.
- Provide AI-generated nutrition tips.

---

## ✨ Key Features

- 👤 User profile collection
- 🏋️ Personalized 7-day workout plan generation
- 🤖 Google Gemini AI integration
- 🎯 Goal-based fitness planning
- ⚡ Workout intensity selection
- 🔄 Workout-plan revision using user feedback
- 🥗 AI-generated nutrition tips
- 💾 Database storage for users and workout plans
- 🌐 Web-based user interface
- 📱 Simple and responsive frontend structure

---

# 🧰 Technology Stack

## Front-End

The frontend is implemented using:

- **HTML5** – Page structure and forms
- **CSS3** – Styling and page layout
- **JavaScript** – Client-side interaction and API communication
- **Jinja2 Templates** – Dynamic HTML rendering through FastAPI

The project uses a traditional server-rendered interface with JavaScript for frontend interaction rather than a React-based frontend.

### Front-End Responsibilities

The frontend is responsible for:

1. Collecting user information.
2. Sending fitness information to the backend.
3. Displaying the generated workout plan.
4. Sending feedback for plan modification.
5. Displaying nutrition tips.
6. Providing a simple user-friendly fitness interface.

---

# ⚙️ Back-End

The backend is developed using **Python and FastAPI**.

### Backend Technologies

- **Python**
- **FastAPI**
- **SQLAlchemy**
- **SQLite / SQL database**
- **Pydantic**
- **Jinja2**
- **Google Generative AI Python SDK**
- **python-dotenv**

### Backend Responsibilities

The backend:

1. Receives user information.
2. Validates the input.
3. Stores user information in the database.
4. Sends user fitness information to Gemini AI.
5. Receives the generated workout plan.
6. Stores the workout plan.
7. Returns the result to the frontend.
8. Accepts user feedback.
9. Uses AI to revise the workout plan.
10. Generates nutrition tips.

---

# 🤖 AI Technology Used

## Google Gemini AI

FitBuddy uses **Google Gemini** as the main artificial intelligence technology.

The AI integration is implemented in:

```text
ai_service.py
```

The application uses the Google Generative AI Python library and a Gemini model to generate fitness-related responses.

### AI Model

The project uses:

```text
Gemini 2.5 Flash
```

### AI Features

#### 1. Personalized Workout Generation

The AI receives information such as:

- Name
- Age
- Gender
- Weight
- Fitness goal
- Workout intensity

It then generates a structured **7-day workout plan**.

#### 2. Workout Plan Revision

The user can provide feedback about the generated workout plan.

The feedback is sent back to the AI, which creates a revised plan.

#### 3. Nutrition Tips

The application can request AI-generated nutrition advice according to the user's fitness goal.

### AI Workflow

```text
User Fitness Details
        ↓
FastAPI Backend
        ↓
AI Service
        ↓
Google Gemini AI
        ↓
Personalized Workout Plan
        ↓
Database
        ↓
Frontend Display
```

---

# 🗂️ Project Structure

```text
FitBuddy-AI-Fitness-Plan-Generator-Using-Gemini-Models/
│
├── main.py
├── ai_service.py
├── crud.py
├── database.py
├── models.py
├── schemas.py
├── requirements.txt
├── test_models.py
│
├── templates/
│   └── index.html
│
└── static/
    ├── css/
    │   └── style.css
    │
    └── js/
        └── script.js
```

---

# 📁 File-by-File Explanation

## `main.py`

This is the main FastAPI application file.

It is responsible for:

- Creating the FastAPI application.
- Connecting the application with the database.
- Serving HTML templates.
- Serving static files.
- Creating API endpoints.
- Receiving user fitness information.
- Calling the AI service.
- Saving generated plans.
- Updating workout plans.

### Main API Operations

```text
POST /users
```

Creates or updates a user.

```text
POST /generate_plan
```

Generates a personalized workout plan using Gemini AI.

```text
GET /users/{user_id}/latest_plan
```

Retrieves the user's latest workout plan.

```text
POST /update_plan
```

Updates a workout plan based on user feedback.

```text
GET /nutrition_tip
```

Generates an AI-based nutrition tip.

---

## `ai_service.py`

This file contains the AI logic.

It:

- Loads the Google Gemini API key.
- Configures the Gemini API.
- Creates the Gemini model.
- Builds AI prompts.
- Generates workout plans.
- Revises workout plans.
- Generates nutrition tips.

Example AI model configuration:

```python
genai.GenerativeModel("gemini-2.5-flash")
```

---

## `database.py`

This file manages the database connection.

It is responsible for:

- Creating the database engine.
- Creating database sessions.
- Providing database access to FastAPI.

---

## `models.py`

This file contains the database models.

It defines the structure used to store application data such as:

- User information
- Workout plans
- Feedback

SQLAlchemy is used for database modeling.

---

## `schemas.py`

This file contains Pydantic schemas.

It is used for:

- Input validation.
- Data serialization.
- API request/response structures.

---

## `crud.py`

CRUD means:

```text
C – Create
R – Read
U – Update
D – Delete
```

This file contains database operations for:

- Creating users.
- Reading users.
- Updating users.
- Creating workout plans.
- Reading workout plans.
- Updating workout plans.
- Saving feedback.

---

## `templates/`

This folder contains the frontend HTML files.

```text
templates/
└── index.html
```

`index.html` provides the main web interface and form used to collect fitness information.

---

## `static/`

This folder contains frontend static resources.

```text
static/
├── css/
│   └── style.css
│
└── js/
    └── script.js
```

### `style.css`

Used for:

- Page styling
- Layout
- Colors
- Buttons
- Forms
- Fitness dashboard appearance

### `script.js`

Used for:

- User interactions
- Form submission
- Calling backend APIs
- Displaying generated results
- Updating the page dynamically

---

## `requirements.txt`

This file contains the Python dependencies required to run the project.

Typical technologies used by this project include:

```text
FastAPI
Uvicorn
SQLAlchemy
Pydantic
Jinja2
Google Generative AI
python-dotenv
```

Install dependencies using:

```bash
pip install -r requirements.txt
```

---

## `test_models.py`

This file is used for testing database models and application data structures.

---

# 🔄 Complete Application Workflow

```text
                ┌─────────────────────┐
                │       User          │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │   Frontend / HTML   │
                │ CSS + JavaScript    │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │     FastAPI         │
                │     Backend         │
                └──────────┬──────────┘
                           │
             ┌─────────────┴─────────────┐
             ▼                           ▼
    ┌─────────────────┐        ┌─────────────────┐
    │    Database     │        │   AI Service    │
    │   SQLAlchemy    │        │    Python       │
    └─────────────────┘        └────────┬────────┘
                                        │
                                        ▼
                              ┌──────────────────┐
                              │  Google Gemini   │
                              │       AI         │
                              └────────┬─────────┘
                                       │
                                       ▼
                              Personalized Plan
                                       │
                                       ▼
                              Frontend Display
```

---

# 🧠 What Makes the Project AI-Based?

The project is not just a normal fitness form.

The important AI component is the **personalization layer**.

The user's information is converted into an AI prompt. Gemini analyzes the provided fitness requirements and generates a customized workout plan.

For example:

```text
User Goal → Weight Loss
Intensity → Moderate
Age → User Input
Weight → User Input
        ↓
   Gemini AI
        ↓
Customized 7-Day Workout Plan
```

The AI can also revise the plan when the user provides feedback.

---

# 🔐 API Key Configuration

The Google Gemini API key should be stored as an environment variable.

Example:

```text
GOOGLE_API_KEY=your_api_key_here
```

Do **not** upload your real API key to GitHub.

Add the environment file to `.gitignore`:

```text
.env
```

---

# 🚀 How to Run the Project

## 1. Clone the Repository

```bash
git clone <your-github-repository-url>
```

## 2. Open the Project

```bash
cd FitBuddy-AI-Fitness-Plan-Generator-Using-Gemini-Models
```

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

## 4. Configure Gemini API Key

Create a `.env` file:

```text
GOOGLE_API_KEY=your_google_gemini_api_key
```

## 5. Run FastAPI

```bash
uvicorn main:app --reload
```

## 6. Open the Application

```text
http://127.0.0.1:8000
```

---

# 📌 API Summary

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/users` | Create/update user |
| POST | `/generate_plan` | Generate AI workout plan |
| GET | `/users/{user_id}/latest_plan` | Get latest workout plan |
| POST | `/update_plan` | Revise workout plan |
| GET | `/nutrition_tip` | Generate nutrition tip |

---

# 🌟 Innovative Aspects

### 1. AI-Based Personalization
Workout plans are generated according to individual user information instead of using the same fixed plan for everyone.

### 2. AI Feedback Loop
Users can provide feedback and the AI can revise the workout plan.

### 3. Goal-Based Planning
The generated plan considers the user's fitness goal and preferred intensity.

### 4. AI Nutrition Support
The system can provide nutrition tips related to the selected fitness goal.

### 5. Full-Stack AI Application
The project combines:

```text
Frontend
   +
Python Backend
   +
Database
   +
Generative AI
```

---

# 🛠️ Technologies at a Glance

| Category | Technology |
|---|---|
| Programming Language | Python |
| Frontend | HTML, CSS, JavaScript |
| Backend | FastAPI |
| Database Layer | SQLAlchemy |
| Data Validation | Pydantic |
| Templates | Jinja2 |
| AI | Google Gemini |
| AI Model | Gemini 2.5 Flash |
| Environment Management | python-dotenv |
| API Server | Uvicorn |
| Version Control | Git & GitHub |

---

# 🎓 Project Outcome

FitBuddy demonstrates how Generative AI can be integrated into a web application to provide personalized fitness assistance.

The project combines web development, Python backend programming, database management, API development, and Generative AI into one application.

---

# ⚠️ Disclaimer

FitBuddy is an educational/project application. AI-generated fitness and nutrition suggestions should not be treated as medical advice. Users should consult a qualified fitness or healthcare professional when appropriate.

---

# 👩‍💻 Project

**Project Name:** FitBuddy – AI Fitness Plan Generator Using Gemini Models

**Repository:** GitHub

**Primary AI:** Google Gemini

**Backend:** Python + FastAPI

**Frontend:** HTML + CSS + JavaScript

**Database:** SQLAlchemy-supported database

---

## 📄 License

This project is intended for educational and demonstration purposes.
