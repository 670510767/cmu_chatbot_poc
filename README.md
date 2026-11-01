# **Education:** 
[B.Sc. in Data Science](https://www.ds.science.cmu.ac.th/enroll4ds/) 
— Chiang Mai University



# 🎓 CMU SMART SCHEDULER (AI CHATBOT)
**An Intelligent Assistant System for Educational Planning and Course Scheduling at Chiang Mai University**

This project is a Proof of Concept (PoC) system for automatically extracting curriculum data from all faculties at Chiang Mai University. The goal is to build an AI Chatbot that helps students schedule classes, recommends backup courses, and checks graduation status.

---

## 🛠️ SYSTEM ARCHITECTURE
The system is divided into 3 main components (Microservices):
1. **DATA INGESTION (Backend Pipeline):** A system for extracting data via PDF parsing and Web Scraping.
2. **AI LOGIC ENGINE (Core Brain):** A system for calculating conditions and scheduling classes.
3. **FRONTEND INTERFACE:** A user interaction system via conversational platforms (LINE OA / Discord) or a Web App.

---

## 📅 DETAILED ROADMAP

### PHASE 1: DATA INFRASTRUCTURE
**Goal:** Build a Modular Knowledge Base that computers can process further.
*   **TASK 1.1: Automated Curriculum Extractor (Python)**
    *   Write scripts (e.g., `pdfplumber` or `PyMuPDF`) to read the university's curriculum PDF files.
    *   Or use an LLM API (Gemini/GPT-4) to read the PDF and convert the structure into a `JSON` format (core courses, minor courses, GE, prerequisites).
*   **TASK 1.2: Schedule Web Scraper (Python)**
    *   Write a bot (e.g., `BeautifulSoup` or `Selenium`) to scrape "course offerings/schedules" data from the CMU Registration Office website.
    *   Extract fields: Course code, section, class day-time, exam day-time, and seat availability.

### PHASE 2: CORE AI LOGIC DEVELOPMENT
**Goal:** Create a program to check conditions and generate schedules.
*   **TASK 2.1: Prerequisite Checker**
    *   Write logic to receive student Transcript data (Mock Data) to check if they have passed prerequisite courses, preventing out-of-sequence registration.
*   **TASK 2.2: Degree Audit (Credit Basket)**
    *   Count the completed credits for major, minor, and GE courses, and calculate how many credits are still required in each category.
*   **TASK 2.3: Smart Schedule Builder**
    *   An algorithm to match "required courses" with "available schedules for the current semester," ensuring class times do not overlap.

### PHASE 3: ADVANCED FEATURES DEVELOPMENT
**Goal:** Address actual pain points during the registration period.
*   **TASK 3.1: Exam Clash Detector**
    *   Add logic to scan "midterm/final exam schedules" to filter out courses with overlapping exam times.
*   **TASK 3.2: Plan B Suggester**
    *   A system to immediately prepare fallback options within the same GE category in case the target section is full.
*   **TASK 3.3: Graduation Mock-up**
    *   A Checklist script summarizing the status before requesting graduation.

### PHASE 4: INTEGRATION & API
**Goal:** Connect all the logic together to make it accessible.
*   **TASK 4.1: Build RESTful API (FastAPI)**
    *   Wrap the code from Phase 2 & 3 with `FastAPI` to create Endpoints to receive commands (e.g., `/api/schedule`, `/api/audit`).
*   **TASK 4.2: AI Controller**
    *   Write a Prompt to wrap the system, allowing the AI to translate students' natural language commands and call the correct API.

### PHASE 5: FRONTEND & UX
**Goal:** Create an interface for real user interaction.
*   **TASK 5.1: LINE Chatbot Setup**
    *   Create a LINE Official Account and connect the Webhook to our API (via `ngrok` for local testing or deploy on Render/Heroku).
*   **TASK 5.2: Transcript Uploader (LIFF / Web App)**
    *   Create a small webpage (HTML/JS) for students to upload their PDF files (Transcript) for processing.

---

## 👥 TASK DELEGATION (For a 2-person team)
To work in parallel and reduce Git Conflicts, the following delegation is recommended:

**🧑‍💻 PERSON 1 (Data & Backend Engineer):** 
*   **Responsibilities:** Phase 1 and Phase 4
*   **Main Tasks:** Ensure we have an accurate JSON database and write APIs to receive commands.
*   **Working Folders:** `/data_pipeline`, `/api`

**🧑‍💻 PERSON 2 (AI Logic & Frontend Engineer):** 
*   **Responsibilities:** Phase 2, Phase 3, and Phase 5
*   **Main Tasks:** Write the calculation logic (scheduling algorithms) and connect the LINE Webhook.
*   **Working Folders:** `/logic_engine`, `/frontend`

---

## 🚀 GETTING STARTED
1. Clone this Repository to your local machine.
2. Run the command `python -m venv venv` to create a Virtual Environment.
3. Run the command `pip install -r requirements.txt` (create this file later when you start writing code).

