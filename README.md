# 🎙️ AI-Powered Meeting Intelligence & Automation Workflow

An end-to-end **no-code AI automation workflow built with n8n** that transforms meeting audio recordings into structured meeting intelligence.

The workflow automatically detects a newly uploaded meeting recording, validates the audio format, prevents duplicate processing, transcribes the recording using **Groq Whisper**, analyzes the transcript using a **Groq LLM**, and delivers the final meeting report through **Gmail** while logging the results in **Google Sheets**.

## 🖼️ Workflow Output

<p align="center">
  <img src="workflow%20output.png" alt="AI-Powered Meeting Intelligence Automation Workflow" width="900">
</p>

## 🚀 Workflow Overview

```text
Google Drive
     ↓
New Audio File Trigger
     ↓
Validate Audio File
     ↓
Duplicate Check
     ↓
Download Audio
     ↓
Groq Whisper
     ↓
Meeting Transcript
     ↓
Groq LLM
     ↓
Summary + Key Decisions + Action Items
     ↓
Format Output
     ↙                 ↘
Gmail              Google Sheets
Email Report       Meeting Record
```

## ✨ Key Features

* 🎙️ **Automatic Audio Detection** — Detects newly uploaded meeting recordings in Google Drive.
* 🔍 **Audio Validation** — Processes supported audio formats such as `.mp3`, `.wav`, and `.m4a`.
* 🛡️ **Duplicate Prevention** — Checks Google Sheets before processing to prevent the same meeting file from being processed multiple times.
* 📝 **AI Transcription** — Uses **Groq Whisper (`whisper-large-v3`)** to convert meeting audio into text.
* 🧠 **AI Meeting Analysis** — Uses a Groq LLM to analyze the transcript.
* 📌 **Meeting Summarization** — Generates a concise summary of the discussion.
* 🎯 **Key Decision Extraction** — Identifies decisions explicitly made during the meeting.
* ✅ **Action Item Extraction** — Extracts tasks with the responsible person and deadline when available.
* 📧 **Automated Email Report** — Sends a structured meeting intelligence report through Gmail.
* 📊 **Google Sheets Logging** — Stores meeting summaries, decisions, action items, timestamps, and file names.

## 🧩 Technologies Used

| Technology        | Purpose                                     |
| ----------------- | ------------------------------------------- |
| **n8n**           | Workflow automation and orchestration       |
| **Google Drive**  | Meeting audio storage and trigger           |
| **Groq Whisper**  | Audio transcription                         |
| **Groq LLM**      | Meeting analysis and information extraction |
| **Gmail**         | Automated report delivery                   |
| **Google Sheets** | Meeting records and duplicate detection     |

## 🔄 Workflow Components

### 1. Google Drive Trigger

The workflow starts when a new meeting audio file is uploaded to the configured Google Drive folder.

### 2. Validate Audio File

The workflow validates the uploaded file extension and only continues for supported audio formats:

* `.mp3`
* `.wav`
* `.m4a`

Non-audio files are automatically filtered out.

### 3. Duplicate Check

Before processing, the workflow searches the **Meeting File** column in Google Sheets.

If the file has already been processed, the workflow stops. If the file is new, processing continues.

### 4. Download Audio File

The validated audio file is downloaded from Google Drive and passed to the transcription stage.

### 5. Groq Whisper Transcription

**Whisper Large V3** converts the meeting recording into a text transcript.

```text
Audio → Whisper → Transcript
```

### 6. Groq LLM — Meeting Intelligence

The transcript is analyzed by the LLM to extract structured meeting information:

* **Summary**
* **Key Decisions**
* **Action Items**
* **Task Owner**
* **Deadline**

The prompt instructs the model to extract only information supported by the transcript and avoid inventing decisions or action items.

### 7. Format Output

The generated JSON response is parsed and converted into clean, readable text for the final outputs.

### 8. Automated Gmail Report

The workflow sends a professional meeting intelligence report containing the summary, key decisions, and action items.

### 9. Google Sheets Logging

Each successfully processed meeting is recorded with:

* Timestamp
* Meeting File
* Summary
* Key Decisions
* Action Items

The same **Meeting File** data is also used for duplicate detection.

## 🎯 Use Case

This automation can be used by:

* Remote teams
* Project managers
* Startups
* Client-facing teams
* Product teams
* Operations teams
* AI automation teams

Instead of manually reviewing meeting recordings and preparing notes, the workflow automatically converts meeting audio into actionable, structured information.

## 🔐 Security Note

API credentials and authentication details should **never be hardcoded into workflow files or committed to GitHub**.

Use n8n credentials or environment variables for:

* Groq API credentials
* Google Drive authentication
* Google Sheets authentication
* Gmail authentication

## 📁 Repository Structure

```text
AI-Powered-Meeting-Intelligence-Automation-Workflow/
│
├── Workflow.json
├── workflow output.png
└── README.md
```

## 🧪 Testing

The workflow was tested with multiple real meeting audio files to verify:

* Audio detection
* File validation
* Duplicate prevention
* Audio downloading
* Transcription
* AI summarization
* Key decision extraction
* Action item extraction
* Gmail delivery
* Google Sheets logging

## 🌟 Outcome

This project demonstrates how **Generative AI can be integrated into a real-world business workflow without building a full custom application**.

The automation combines:

**Event Automation + Speech-to-Text + LLM Intelligence + Email Automation + Structured Data Logging**

---

### Built With

**n8n · Groq Whisper · Groq LLM · Google Drive · Gmail · Google Sheets**

### Author

**Waariha Asim**

AI Engineer | AI Automation Engineer
