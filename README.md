🤖 BellMedEx Meta-Agent – Automated Hiring & Interview Workflow

🚀 Overview

The BellMedEx Meta-Agent is a fully automated AI-powered hiring assistant built with n8n.
It simplifies and streamlines the entire recruitment lifecycle — from application submission to interview scheduling — using AI, automation, and smart integrations.

This workflow automates:
	•	Application intake via an interactive form
	•	Candidate confirmation and acknowledgment emails
	•	HR decision routing (accept/reject)
	•	AI-generated personalized response emails
	•	Automated interview scheduling with Google Calendar and Google Meet
	•	Candidate confirmation follow-ups

<img width="1440" height="900" alt="Screenshot 2025-10-06 at 5 03 23 PM" src="https://github.com/user-attachments/assets/1a035fad-f645-467a-a340-bf76d24c6b0f" />
<img width="1440" height="900" alt="Screenshot 2025-10-06 at 5 03 40 PM" src="https://github.com/user-attachments/assets/9790a5bf-478e-47ac-b64e-9fbd5a030869" />


🧩 Core Components

Module	Description
Form Trigger (Easy Apply)	Collects candidate data such as Full Name, CNIC, CV, reason for joining BellMedEx, technical role, experience, salary expectations, and notice period.
Applying Confirmation Email	Sends an automated acknowledgment email to applicants confirming receipt of their submission.
AI Data Formatter Agent	Extracts and summarizes the applicant’s details into a clean, structured format for the HR team.
Hiring Team Approval Email	Sends a double-option (approve/reject) email to the hiring team for each applicant.
Decision Router (Switch Node)	Routes workflow based on HR’s approval status — triggers “Accepted” or “Rejected” email automation accordingly.
Groq & OpenRouter Models	Uses AI models (Gemma, Qwen, and DeepSeek) to generate professional HR responses for approved or rejected candidates.
Accepted / Rejected Email Templates	Professionally crafted AI prompts ensure polite, empathetic, and personalized communication for every candidate.
AI Interview Scheduling Agent	Automatically finds the next available interview slot, creates a Google Meet link, and adds it to Google Calendar.
Candidate Interview Confirmation	Sends a “Send and Wait” approval email allowing the applicant to confirm or decline the proposed schedule.



⚙️ Workflow Logic

🧠 Step-by-Step Flow
	1.	Form Submission (On Form Submission)
	•	The workflow starts when an applicant fills out the “Easy Apply” form.
	•	Required inputs include:
	•	Full Name
	•	CNIC
	•	Uploaded CV (PDF)
	•	Reason for joining BellMedEx
	•	Proficiency area (Frontend, Backend, or AI Engineer)
	•	Current and expected salary
	•	Years of experience
	•	Notice period
	•	Email
	2.	Applicant Acknowledgment
	•	Immediately sends an automated confirmation email acknowledging the submission.
	3.	Information Relay to HR
	•	A “Smart Agent” compiles candidate info and sends it to the hiring team, attaching the CV and all form details.
	4.	HR Approval Request
	•	The hiring team receives an approval email with two buttons — Approve or Reject — and up to 2 days to respond.
	5.	Conditional Routing
	•	If HR approves, an AI-generated shortlisting email is sent to the applicant.
	•	If HR rejects, an AI-generated polite rejection email is sent.
	6.	Interview Scheduling (If Approved)
	•	The AI Scheduling Assistant automatically finds the next available 1-hour interview slot:
	•	3 days after the shortlist email is sent
	•	Between 10:00 AM and 7:00 PM
	•	Avoids lunch (1:00–2:30 PM) and tea (5:00–5:30 PM) breaks
	•	If the day is fully booked, it automatically checks the next available day.
	•	Creates a Google Meet link and adds it to the Google Calendar event.
	7.	Candidate Interview Confirmation
	•	Sends the applicant a confirmation email with “I am available” / “I won’t be available” buttons.
	8.	Final Confirmation to HR
	•	HR receives a summary email containing the candidate’s response and meeting details.


🧠 AI Models Integrated

Provider	Model	Purpose
Groq	Gemma 2 9B IT, Qwen 32B	HR communication & scheduling logic
OpenRouter	DeepSeek v3.1	Generates empathetic and professional applicant emails
LangChain Agents	n8n-native AI orchestration	Connects models, memory, and tools dynamically



🔧 Integrations

Integration	Purpose
Google Calendar	Checks available slots, creates events, and attaches Meet links.
Google Meet	Auto-generates virtual interview links for each candidate.
SMTP Email (Gmail)	Sends automated emails (confirmation, approval, rejection, interview scheduling).
Groq + OpenRouter APIs	Power the conversational AI logic for HR automation.


🧱 Form Fields (Front-End View)

Field	Type	Required	Notes
Full Name	Text	✅	Applicant’s full name
CNIC	Number	✅	Applicant’s national ID
CV	File (PDF)	✅	Must be a PDF
Why join BellmedEx	Text	✅	Motivation statement
What are you most proficient in?	Dropdown	✅	Front-end / Back-end / AI Engineer
Current Salary	Number	✅	Optional if unemployed
Expected Salary	Number	✅	-
Experience (Years)	Text	✅	Total years in the field
Website	Text	❌	Personal portfolio link
Notice Period	Number	✅	Days required before joining
Email	Email	✅	For communication


📅 Interview Scheduling Logic

Rules Implemented by AI Agent:
	•	Start date: 3 days after shortlist mail
	•	Working hours: 10:00 AM – 7:00 PM
	•	Breaks: 1:00–2:30 PM (Lunch), 5:00–5:30 PM (Tea)
	•	Duration: 1 hour per interview
	•	Rolls over to next available day if full
	•	Generates Google Meet + Calendar event
	•	Sends confirmation to both HR and the applicant

💡 Key Highlights
	•	🤖 End-to-end automation — no manual HR intervention needed
	•	✉️ AI-personalized communication for acceptance & rejection
	•	📅 Dynamic scheduling with calendar conflict resolution
	•	🧠 Multi-model orchestration with memory-aware AI
	•	📎 Attachment handling for applicant CVs
	•	🔁 Approval loop ensures HR remains in control
	•	☁️ Easily deployable on local or cloud n8n instances


⚙️ Setup Guide
	1.	Install n8n
Follow official setup: https://docs.n8n.io/
	2.	Import the Workflow
	•	Upload meta-agent.json into your n8n editor via Import → Workflow.
	3.	Connect Credentials
	•	Google Calendar OAuth2
	•	SMTP (Gmail)
	•	Groq API
	•	OpenRouter API
	4.	Activate the Workflow
	•	Turn on the workflow toggle in n8n to make the form live.
	5.	Share the Public Form
	•	Use your n8n deployment URL (e.g., https://yourdomain.com/form/23e9ff48-fde7-4f5e-8368-e6f2a3a01725)
	•	Share it with candidates for easy application submission.


📬 Output Example

Candidate Confirmation Email

Subject: Thank you for applying to BellMedEx!

Dear Ameer,
We’ve received your application and CV. Our hiring team will review your details and reach out if shortlisted.
Meanwhile, visit our website at https://bellmedex.com to learn more about us.

Shortlist Email

Subject: Congratulations – You’ve Been Shortlisted for AI Engineer

Dear Ameer,
We’re pleased to inform you that you’ve been shortlisted for the interview round for the AI Engineer role.
Your interview is scheduled on 10/09/2025 at 10:00 AM.
Join via: https://meet.google.com/abc-xyz-123


If you have any questions or suggestions, feel free to reach out at
🌐 Mortaza76.github.io
<img width="1440" height="900" alt="Screenshot 2025-10-06 at 5 04 27 PM" src="https://github.com/user-attachments/assets/0c6b8baf-107c-4848-aa3c-326707864163" />
<img width="1440" height="900" alt="Screenshot 2025-10-06 at 5 04 35 PM" src="https://github.com/user-attachments/assets/5f445774-9e99-4dfe-9668-cee0c51cd1c1" />
<img width="1440" height="900" alt="Screenshot 2025-10-06 at 5 04 42 PM" src="https://github.com/user-attachments/assets/90053947-c305-4285-93a2-da4a91df8988" />
<img width="1440" height="900" alt="Screenshot 2025-10-06 at 5 05 00 PM" src="https://github.com/user-attachments/assets/d8605c30-e44d-4915-a6ca-f686dfd75746" />
<img width="1440" height="900" alt="Screenshot 2025-10-06 at 5 05 22 PM" src="https://github.com/user-attachments/assets/ed9c3786-6a4c-4935-970c-dfd43dff352f" />




