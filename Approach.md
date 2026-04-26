# Project Write-up: AI Skill Assessment & Learning Plan

## 1. Approach & Objective
The core objective of this project is to automate the technical screening process by moving beyond static keyword matching. The system acts as an **expert Technical Skills Assessor** that conducts a forensic comparison between a Job Description (JD) and a Resume, followed by a live validation interview.

The system follows a 4-phase agentic lifecycle:
1. **Forensic Analysis:** Silently identifying required skills and comparing them to the uploaded resume.
2. **Sequential Validation:** Asking one-by-one, scenario-based technical questions to verify actual proficiency.
3. **The Iteration Loop:** Maintaining state to ensure every identified skill is assessed before finalizing.
4. **Strategic Reporting:** Generating an actionable HTML report with gaps, learning plans, and time estimates.

## 2. Technical Architecture
The solution is orchestrated via **n8n**, utilizing a modular, local-first architecture:

* **Trigger & Ingestion:** Uses a `FormTrigger` for the JD and a `Form` node for candidate details and PDF resume uploads.
* **File Extraction:** The `Extract from File` node handles the conversion of PDF binary data into text, ensuring data remains within the workflow execution.
* **Context Priming:** A JavaScript `Code` node ("Prime Context") structures the initial payload, ensuring the AI begins Phase 1 with all necessary context without manual intervention.
* **Intelligence Engine:** Powered by an `AI Agent` using the **Gemini 2.0 Flash** model. This provides high-speed reasoning and massive context window capabilities.
* **Memory Management:** A `Window Buffer Memory` node ensures the agent remembers previous answers throughout the long interview process.
* **Logical Routing:** An `If` node acts as a "State Guard." It checks the AI's output for a completion signal ("Validated Proficiencies"). If found, it routes to reporting; if not, it loops back to the interview form.
* **Output Sanitization:** Custom JavaScript nodes sanitize raw AI output for the web form and generate a professional, styled **HTML Report** for the final assessment.

## 3. Trade-offs & Design Decisions
* **Model Selection (Gemini 2.0 Flash):** Chosen for its exceptional speed and efficiency in long-context conversations compared to traditional GPT models.
* **Local-First Processing:** By extracting PDF text directly in n8n, we avoid using external third-party PDF parsing APIs, increasing data privacy.
* **Looping Mechanism:** Instead of a single long form, the workflow uses a "Recursive Loop" via n8n forms, which makes the experience feel like a real-time chat for the candidate.
* **State Signal:** Using a specific string ("Validated Proficiencies") as a trigger for the final report is a lightweight but effective way to manage agentic state without a database.
