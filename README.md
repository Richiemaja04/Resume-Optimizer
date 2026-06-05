# ResumeIQ — AI-Powered Resume Optimizer

> Beat the ATS. Land the interview. Built with FastAPI + OpenAI + spaCy + SentenceTransformers.

<img width="1901" height="977" alt="image" src="https://github.com/user-attachments/assets/79bcb0bd-0f35-43ca-a2bd-4a04ae7b5061" />

<img width="1894" height="978" alt="image" src="https://github.com/user-attachments/assets/d85ec266-9aa2-4f77-986c-c949c440c0c2" />

<img width="1899" height="979" alt="image" src="https://github.com/user-attachments/assets/d156515b-31dd-4bba-96eb-3f3057c89cae" />


---

## 🏗 Project Structure

```
resume-optimizer/
├── index.html              # Landing page
├── builder.html            # 5-step resume builder wizard
├── dashboard.html          # ATS analytics dashboard
├── css/
│   ├── styles.css          # Main styles (dark theme, components)
│   └── animations.css      # Transitions, keyframes, loading states
├── js/
│   ├── app.js              # Builder wizard, nav, interactions
│   └── charts.js           # Chart.js analytics (skill, section, donut, timeline)
├── templates/
│   ├── classic.html        # ATS-safe classic template
│   ├── modern.html         # Two-column modern template
│   └── technical.html      # Developer-focused template
├── static/
│   └── generated_resumes/  # AI-generated output files
└── backend/
    ├── main.py             # FastAPI app + routes
    ├── db.py               # SQLite schema + queries
    ├── models.py           # Pydantic request/response models
    ├── services.py         # Core AI/NLP logic
    ├── utils.py            # File handling, PDF/DOCX conversion
    └── requirements.txt    # Python dependencies
```

---

## 🚀 Quick Start

### 1. Frontend (open directly in browser)
```bash
# Just open index.html in any modern browser
open index.html
```

### 2. Backend API

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Download spaCy model
python -m spacy download en_core_web_sm

# Set API keys
export OPENAI_API_KEY=sk-...

# Run server
uvicorn main:app --reload --port 8000
```

API docs: `http://localhost:8000/docs`

---

## 📐 ATS Scoring Formula

```
ATS Score = 0.4 × Keyword Match
          + 0.3 × Skill Match        (semantic similarity via SentenceTransformers)
          + 0.2 × Experience Match   (semantic similarity of experience vs JD)
          + 0.1 × Formatting Score   (rules-based: sections, contact info, length)
```

---

## 🔑 Key API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/profile` | Save user profile, get template recommendations |
| POST | `/api/analyze/upload` | Upload resume + JD → ATS analysis + optimized output |
| POST | `/api/analyze/scratch` | Build from scratch → AI-generated + analyzed resume |
| GET  | `/api/download/{filename}` | Download optimized resume as PDF or DOCX |
| GET  | `/api/templates` | List available ATS-friendly templates |

---

## 🤖 AI/NLP Pipeline

1. **Parse** — pdfplumber (PDF) or python-docx (DOCX) extracts full text  
2. **Segment** — regex + heuristics split text into sections (summary, experience, skills, education)  
3. **Extract** — spaCy NER + curated patterns pull skills, entities, keywords  
4. **Score** — SentenceTransformer embeddings compute semantic similarity  
5. **Enhance** — GPT-4o-mini rewrites bullets, injects keywords, strengthens summary  
6. **Render** — Content fitted into selected HTML template → PDF/DOCX export  

---

## 🎨 Frontend Tech

- **Fonts**: Syne (headings) + DM Sans (body)
- **Animations**: AOS (scroll reveal) + CSS keyframes
- **Charts**: Chart.js 4.4 (bar, horizontal bar, doughnut, line)
- **Theme**: Dark mode, CSS custom properties, glassmorphism elements

---

## ⚙️ Environment Variables

```env
OPENAI_API_KEY=sk-...
# GEMINI_API_KEY=...     # Optional: swap to Gemini
```

---

## 📄 License

MIT — free to use, modify, and deploy.
