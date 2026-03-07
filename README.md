# Traceback 🔍
### AI-Powered Student Learning Diagnostics System

> *Most systems tell students they failed. Traceback tells them why.*

Traceback analyzes student behavioral and performance signals to identify the **root cause** of academic struggle — then generates a personalized, actionable learning plan for each student.

---

## 🌐 Live Demo

| Interface | Link |
|-----------|------|
| 🎓 Student Portal | [leenabdulkareemcs.github.io/Traceback/student.html](https://leenabdulkareemcs.github.io/Traceback/student.html) |
| 📊 Professor Dashboard | [leenabdulkareemcs.github.io/Traceback/dashboard.html](https://leenabdulkareemcs.github.io/Traceback/dashboard.html) |

**Try these student IDs in the portal:** `125535` · `623831` · `566133` · `697492` · `565513`

---

## 📌 The Problem

Current educational systems have three critical gaps:

- Grades are reported but **not explained**
- Professors teaching 200+ students **cannot individually diagnose** each student
- Generic advice (*"study more"*) is given to all students regardless of their actual problem

The same symptom — a low score — can have completely different root causes:

| Root Cause | What it looks like | What they actually need |
|------------|-------------------|------------------------|
| NO_ENGAGEMENT | Low score + almost no platform activity | Habit building + attendance |
| KNOWLEDGE_GAP | Low score + high engagement + multiple attempts | Go back to prerequisites |
| DECLINING | Was passing, now failing | Identify what changed |
| EXAM_ANXIETY | Good coursework, poor formal assessments | Assessment technique training |
| NEEDS_SUPPORT | Consistent but just below threshold | Targeted topic intervention |

---

## 🏗️ System Architecture

```
Layer 1 — WHAT      (grades, scores, pass/fail)
         ↓
Layer 2 — HOW       (behavioral signals — what we built ✅)
         ↓
Layer 3 — WHY       (answer analysis — v2 roadmap)
```

Two interfaces, two users:

```
STUDENT PORTAL          →  Personal diagnosis + learning plan
PROFESSOR DASHBOARD     →  Class-wide analytics + urgency breakdown
```

---

## 📊 Key Results

| Metric | Value |
|--------|-------|
| Students analyzed | 28,785 |
| Classifier accuracy | **92.5%** (XGBoost) |
| Plans generated | 28,785 |
| Students needing intervention | 8,449 (29.3%) |

### Engagement predicts outcome

| Final Result | Avg Score | Avg VLE Clicks |
|-------------|-----------|----------------|
| Distinction | 87.9 | 28.0 |
| Pass | 75.7 | 19.4 |
| Fail | 53.0 | 6.5 |
| Withdrawn | 28.8 | 3.0 |

Distinction students engage **9x more** than Withdrawn students.

### Root cause distribution

| Root Cause | Students | % | Urgency |
|------------|----------|---|---------|
| ON_TRACK | 13,134 | 45.6% | 🟢 LOW |
| NO_ENGAGEMENT | 5,812 | 20.2% | 🔴 CRITICAL |
| EXAM_ANXIETY | 4,433 | 15.4% | 🟡 MEDIUM |
| NEEDS_SUPPORT | 2,769 | 9.6% | 🟡 MEDIUM |
| DECLINING | 2,637 | 9.2% | 🟠 HIGH |

---

## ⚙️ Technical Pipeline

### Step 1 — Data Cleaning & Merging
- 7 OULAD CSV files cleaned and merged
- 28,785 students × 32 columns in master table
- Calculated submission timing, score trends, dropout flags

### Step 2 — Feature Engineering
- 10 signals normalized (MinMaxScaler)
- 3 composite risk scores built:
  - `academic_risk` = low score + declining trend + inconsistency
  - `engagement_risk` = low clicks + few resources + no early submissions
  - `persistence_risk` = prev attempts + late submissions + dropout signal
- 5 root cause labels assigned per student

### Step 3 — Root Cause Classifier

| Model | Accuracy |
|-------|----------|
| Decision Tree | 89.7% |
| Random Forest | 90.4% |
| **XGBoost** | **92.5% ✅** |

Top 3 most important features:
1. `avg_score_norm` → 45.2% of model decision
2. `academic_risk` → 18.3%
3. `score_trend_norm` → 13.8%

### Step 4 — Learning Plan Generator
- Rule-based engine using each student's real signal values
- 4-step personalized plan per student
- Plain-English diagnosis with actual numbers

---

## 🖥️ Interfaces

### Student Portal
Light, warm, personal interface:
- Login with student ID
- Root cause diagnosis in plain language
- 6 performance signals
- 3 animated risk bars
- 4-step personalized learning plan
- Personalized encouragement message

### Professor Dashboard
Dark, analytical interface:
- Root cause distribution chart
- Intervention urgency breakdown
- Average score by root cause
- Engagement vs final result
- System KPIs
- Student search by ID

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Data Processing | Python, pandas, numpy |
| Machine Learning | scikit-learn, XGBoost |
| Visualization | matplotlib, seaborn |
| Development | Google Colab |
| Frontend | HTML5, CSS3, JavaScript |
| Hosting | GitHub Pages |
| Dataset | OULAD (Open University) |

---

## 📁 Repository Structure

```
Traceback/
├── README.md                    ← this file
├── Traceback_Documentation.docx ← full project report
├── Traceback.ipynb              ← full ML pipeline (Colab notebook)
├── dashboard.html               ← professor view
└── student.html                 ← student portal
```

---

## 🗺️ Roadmap

- [x] **Stage 1** — Analysis engine + both interfaces (complete ✅)
- [ ] **Stage 2** — Progress tracking + plan completion system
- [ ] **Stage 3** — Answer analysis engine (v2)
  - Students answer CS questions inside Traceback
  - Error classification: concept vs misunderstanding vs application
  - Prerequisite mapping (fails recursion → check functions first)
- [ ] **Stage 4** — AI tutor integration (Gemini/Claude API)
  - Conversational tutoring
  - Custom exercise generation
  - Real-time feedback

---

## 📂 Dataset

[OULAD — Open University Learning Analytics Dataset](https://analyse.kmi.open.ac.uk/open_dataset)

Anonymized real student data from the UK Open University. 7 CSV files covering student demographics, assessment scores, registration, and virtual learning environment interactions.

---

## 👩‍💻 Author

**Leen Abdulkareem**
GitHub: [@leenabdulkareemcs](https://github.com/leenabdulkareemcs)

---

*Traceback — Diagnose. Plan. Improve.*
