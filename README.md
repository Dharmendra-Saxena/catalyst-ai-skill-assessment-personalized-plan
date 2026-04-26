# AI Skill Assessment & Personalized Learning Plan

An intelligent n8n-based orchestration that automates technical skill gap analysis and candidate interviewing.

## 🚀 Features
- **Forensic Skill Mapping:** Compares Job Descriptions against Resumes to identify "Likely Proficiencies" and "Potential Gaps."
- **Interactive Interviewer:** Asks one-by-one scenario-based technical questions to validate real-world knowledge.
- **Automated Reporting:** Generates a styled HTML report including Validated Proficiencies, Gaps, and a Personalized Learning Plan.
- **Privacy-Centric:** Processes PDFs locally within the workflow.

## 🛠️ Tech Stack
- **n8n:** Workflow automation and form UI.
- **LangChain:** For agentic reasoning and memory management.
- **OpenAI GPT-4o-mini:** The intelligence engine.
- **JavaScript:** Custom data sanitization and HTML report formatting.

## 📋 Prerequisites
- An n8n instance (Desktop or Cloud).
- OpenAI API Key.

## ⚙️ Setup & Installation
1. **Download the Workflow:** Download the `Catalyst_AI_Skill_Assessment_Personalized_Learning_Plan_final.json` file from this repository.
2. **Import to n8n:**
   - Open your n8n dashboard.
   - Click on **Workflows** > **Add Workflow** > **Import from File**.
   - Select the JSON file.
3. **Configure Credentials:**
   - Open the **OpenAI Chat Model** node.
   - Select your OpenAI credentials or create new ones using your API key.
4. **Deploy:**
   - Click **Execute Workflow** to test or **Save** and toggle **Active** to use the public Webhook URLs for the forms.

## 📖 How it Works
1. **Submit JD:** Enter the detailed Job Description in the first form.
2. **Upload Resume:** Provide the candidate's email and upload their resume (PDF).
3. **The Interview:** The AI will ask questions one-by-one based on the JD's requirements.
4. **Final Report:** Once all skills are assessed, the workflow displays a formatted report with a "Save as PDF" option.
