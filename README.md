# AI Skill Assessment & Personalized Learning Plan

An intelligent n8n-based orchestration that automates technical skill gap analysis and candidate interviewing using Gemini 2.0 Flash.

## 🚀 Features
- **PDF Extraction:** Locally processes resumes to extract skills without external cloud storage.
- **Agentic Interviewing:** Asks scenario-based technical questions one-by-one based on JD requirements.
- **Stateful Memory:** Remembers candidate answers to provide a holistic final evaluation.
- **HTML Reporting:** Generates a beautiful, printable report with learning plans and time estimates.

## 🛠️ Tech Stack
- **n8n:** Workflow automation and user interface.
- **Google Gemini 2.0 Flash:** The core LLM for reasoning and interviewing.
- **LangChain:** For agent memory and orchestration.
- **JavaScript:** For data cleaning and HTML styling.

## 📋 Prerequisites
- An n8n instance.
- A Google Gemini (AI Studio) API Key.

## ⚙️ Setup & Installation
1. **Import Workflow:** - Download the `Catalyst_AI_Skill_Assessment_Personalized_Learning_Plan.json` file.
   - In n8n, go to **Workflows** > **Add Workflow** > **Import from File**.
2. **Configure Credentials:**
   - Open the **Google Gemini Chat Model** node.
   - Add your API Key under the "Google Gemini(PaLM) Api" account section.
3. **Activate:** - Save the workflow and toggle the **Active** switch.
4. **Use:** - Open the URL of the "On form submission" node to start the process with a Job Description.

## 📖 How to Demo
1. Submit a technical Job Description in the first form.
2. Enter a candidate email and upload a resume PDF in the second form.
3. Answer the technical questions posed by the AI.
4. Once finished, view and "Save as PDF" the final assessment report.
