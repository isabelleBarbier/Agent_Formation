# 🎓 Intelligent Multi-Agent Educational Quiz System

[![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?logo=kaggle&logoColor=fff)](https://www.kaggle.com/) [![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=fff)](https://www.python.org/) [![ADK](https://img.shields.io/badge/Agent_Development_Kit-4285F4?logo=google&logoColor=fff)](https://google.github.io/adk-docs/) [![Gemini API](https://img.shields.io/badge/Gemini_API-4285F4?logo=google&logoColor=fff)](#)  


> An intelligent pedagogical assessment system based on Google ADK and
> Gemini, designed to automate the creation, adaptation, and
> personalized tracking of educational quizzes.

## 📋 Table of Contents

-   [Overview](#overview)
-   [Architecture](#architecture)
-   [Features](#features)
-   [Installation](#installation)
-   [Configuration](#configuration)
-   [Usage](#usage)
-   [Adaptation for Other
    Environments](#adaptation-for-other-environments)

## 🎯 Overview

This project implements a multi-agent system using the Google ADK (Agent
Development Kit) architecture to create a personalized and scalable
learning experience. It solves a major issue for instructors: **the
time-consuming creation of adapted assessments**.

### Problem Solved

Instructors spend alot of time (too much...) per assessment module:
- Analyzing the content to assess
- Creating varied questions adapted to different levels
- Manually correcting submissions
- Writing personalized feedback

**This system automates the entire workflow in just a few minutes.**

## 🏗️ Architecture

The system is built around **4 specialized AI agents** coordinated by an
intelligent orchestrator:

    QuizAgent (Coordinator)
    ├── AnalyserAgent (Subject analysis)
    ├── QuestionAgent (Question generation)
    ├── ExplanationAgent (Pedagogical explanations)
    └── FeedbackAgent (Personalized feedback)

### Agents

| Agent | Rôle | Model |
|-------|------|--------|
| **AnalyserAgent** | Break down the subject into key concepts, identify prerequisites, and assess complexity | Gemini 2.5 Flash Lite |
| **QuestionAgent** | Generates questions adapted to the level (true/false, multiple choice, exercises) | Gemini 2.5 Flash Lite |
| **ExplanationAgent** | Create detailed explanations with examples and analogies | Gemini 2.5 Flash Lite |
| **FeedbackAgent** | Produces constructive and personalized feedback | Gemini 2.5 Flash Lite |
| **QuizAgent** | Coordinates agents, makes contextual decisions, manages proactivity | Gemini 2.5 Flash Lite |

A SequentialAgent would be much better than LlmAgent for coordination : it would always impose the same order of execution.
Despite this, decision-making, proactivity (to anticipate needs), and creativity were given priority in this project.
It is this adaptive intelligence that makes all the difference. The system does not simply execute, it thinks and adapts.


### Tools

The system relies on four state-management tools: 
-`save_user_profile()` : Saves the user's profile (name, level, weaknesses).
- `get_user_profile()` : Retrieve the user's profile.
- `save_quiz_result()` : Saves quiz results.
- `get_learning_progression()` : Analyze the progress (average score, trend, recurring weaknesses).

## ✨ Features

### Automatic Personalization

-   Level-adapted questions (beginner/intermediate/advanced)
-   Unique questions for each user
-   Explanations adapted to the level of understanding

### Progress Tracking

-   Full quiz history
-   Weakness detection
-   Trend analysis (improvement/stagnation)
-   Average score tracking

### Adaptive Intelligence

-   The coordinator makes contextual decisions
-   Proactive: suggesting revisions, changing approach if failures are repeated
-   Dynamic difficulty

## 🚀 Installation

### Kaggle Environment

Optimized for Kaggle with ADK and Gemini preconfigured.

Steps: 1. Upload notebook 2. Import in Kaggle 3. Enable Internet 4. Run

## 🔧 Configuration

### Environment Variables (if necessary)
Gemini API configuration (usually automatic on Kaggle)

``` python
import os
os.environ['GOOGLE_API_KEY'] = 'your_api_key'
```

### Retry Configuration

``` python
retry_config = types.HttpRetryOptions(
    attempts=5,
    exp_base=7,
    initial_delay=1,
    http_status_codes=[429, 500, 503, 504],
)
```

## 💻 Usage

``` python
response = root_agent.run("My name is Paul and I want to create a quiz on photography for beginners")
response = root_agent.run("My name is Asma, generate a quiz about Machine learning, expert level")
response = root_agent.run("Create 5 questions on Python, intermediate level")
```

### Workflow

1.  Register profile\
2.  System analyzes subject\
3.  Quiz generation\
4.  User answers\
5.  Feedback\
6.  Saving & tracking

## 🔄 Adaptation for Other Environments

### Google Colab

``` python
!pip install google-genai google-adk
from google.colab import userdata
import os
os.environ['GOOGLE_API_KEY'] = userdata.get('GOOGLE_API_KEY')
from google.adk.tools import ToolContext
```

### Local Environment

requirements.txt:

    google-genai>=0.3.0
    google-adk>=0.1.0
    typing-extensions>=4.5.0

Installation:

``` bash
# Create a virtual environment
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
# Install the dependencies
pip install -r requirements.txt
# Configure the API key
export GOOGLE_API_KEY='your_api_key'
```
### .env.example file
```env
GOOGLE_API_KEY=votre_clé_api_gemini
MODEL_NAME=gemini-2.5-flash-lite
MAX_RETRY_ATTEMPTS=5
```

### Modifications needed depending on the environment

 Environnement | Changes requised |
|---------------|------------------------|
| **Kaggle** | ✅ None (optimized) |
| **Google Colab** | Installation of packages +  API key configuration |
| **Local** | Complete installation + environment variables management |


## 🎓 Use Cases

### Instructors

-   Automatic quiz creation
-   Progress tracking
-   Saves time for module creation




### Improvements

-   [ ] Interactivity
-   [ ] Multilingual support
-   [ ] Result export
-   [ ] Web UI
-   [ ] Support other models
-   [ ] Gamification


### 🙏 Acknowledgments

-   Google ADK\
-   Gemini API\
-   Kaggle

This project is an educational project. It was made for the challenge 5 Day AI Agents Intensive (Kaggle, Google).
It remains to improve...


