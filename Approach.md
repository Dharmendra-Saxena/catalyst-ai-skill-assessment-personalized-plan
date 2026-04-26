# Project Write-up: AI Skill Assessment & Personalized Learning Plan

## 1. Approach & Objective
The core objective of this project is to transform the traditional, static resume screening process into a dynamic, interactive experience. Instead of a simple keyword match, this system acts as an **expert Technical Skills Assessor**. 

The approach is built on a **four-phase agentic lifecycle**:
1.  **Forensic Analysis:** Silently extracting required skills from a Job Description (JD) and comparing them against a candidate's resume to identify potential gaps.
2.  **Sequential Validation:** Engaging the candidate in a one-by-one interview process using scenario-based technical questions to verify "Actual Proficiency" versus "Theoretical Knowledge".
3.  **Iteration Loop:** Maintaining state through a conversation history to ensure every identified skill is addressed.
4.  **Strategic Reporting:** Generating a comprehensive final report that doesn't just list failures but provides a roadmap for growth.

## 2. Technical Architecture
The solution is orchestrated via **n8n**, utilizing a modular architecture to handle data flow and AI reasoning:

* **Data Ingestion:** Uses a `FormTrigger` to capture the JD and a secondary `Form` node for candidate details and PDF resume uploads.
* **File Processing:** The `Extract from File` node converts binary PDF data into raw text for AI consumption.
* **Context Priming:** A JavaScript `Code` node ("Prime Context") structures the initial prompt, ensuring the AI enters Phase 1 with all necessary documents without further user prompting.
* **Intelligence Engine:** An `AI Agent` node powered by **OpenAI’s gpt-4o-mini**. This is paired with a `Window Buffer Memory` to maintain context over long, multi-question interviews while staying within token limits.
* **Control Flow (The Loop):** An `If` node monitors the AI's output. It detects a specific "Final Report Signal" (`Validated Proficiencies`) to decide whether to continue the interview via `Form1` or finalize the process.
* **Output Formatting:** Dual JavaScript nodes sanitize and style the output—one for plain-text UI interaction and another that generates a professional, styled **HTML Report** for the final assessment.

## 3. Trade-offs & Design Decisions
* **Model Selection:** We utilized **gpt-4o-mini** to balance high-level reasoning with cost-efficiency, ensuring the tool remains scalable for high-volume recruitment.
* **User Interface:** By using **n8n's native form nodes**, we eliminated the need for a separate frontend hosting environment, reducing complexity and ensuring data stays within the workflow.
* **Sanitization Logic:** Custom regex-based JavaScript nodes were implemented to ensure that AI-generated Markdown or special characters don't break the form's JSON structure, leading to a smoother user experience.
* **Privacy:** The "zero-cloud" footprint philosophy is respected by processing the binary PDF data directly in memory during the execution rather than storing files in external databases.

## 4. Conclusion
This architecture demonstrates how low-code tools like n8n can be combined with sophisticated AI agent logic to solve complex, domain-specific problems—moving beyond simple automation and into the realm of intelligent, autonomous assistance.
