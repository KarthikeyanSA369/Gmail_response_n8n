# Gmail AI Auto-Responder

### Intelligent Email Processing & Automated Response Generation Using AI and n8n

<p align="center">   An AI-powered Gmail automation system that monitors incoming emails, filters messages using configurable sender conditions, generates intelligent and professional responses using Groq's Llama 3.3 70B model, and automatically delivers replies through Gmail using n8n.</p>

---



An AI-powered Gmail automation workflow built using **n8n, Groq API and Llama 3.3 70B**. The system monitors incoming emails, checks configured sender conditions, generates professional responses using an AI language model and sends the generated response through Gmail.

---

## Project Overview

Managing repetitive emails manually can consume valuable time. Gmail AI Auto-Responder simplifies this process by combining workflow automation with large language models.

The workflow automatically detects incoming emails, evaluates a configured sender condition, processes matching email content using an AI model and delivers the generated response through Gmail.

The project demonstrates how AI and low-code automation can work together to build an intelligent email response system.

## Key Features

- **Automated Gmail Monitoring** – Detects incoming emails using Gmail Trigger.
- **Sender-Based Filtering** – Checks incoming email sender information against a configured condition.
- **AI-Powered Response Generation** – Uses an LLM to generate professional email replies.
- **Groq API Integration** – Connects to Groq's language model service.
- **Llama 3.3 70B** – Uses the `llama-3.3-70b-versatile` model.
- **Automated Email Delivery** – Sends generated responses using Gmail.
- **Workflow Orchestration** – Connects all processing stages through n8n.

## Workflow Architecture

```text
       INCOMING GMAIL
              |
              v
        GMAIL TRIGGER
        (Every Minute)
              |
              v
        IF CONDITION
       (Sender Check)
              |
              v
       BASIC LLM CHAIN
              |
              v
       GROQ CHAT MODEL
       LLAMA 3.3 70B
              |
              v
      AI-GENERATED REPLY
              |
              v
        GMAIL SEND
              |
              v
       EMAIL DELIVERED
```

*The workflow continues through the matching sender-condition branch. Non-matching emails do not enter the AI response path.*

## How It Works

### 1. Gmail Trigger

The Gmail Trigger monitors the connected Gmail account and checks for incoming emails every minute.

### 2. Sender Condition

The IF node evaluates the sender information against a configured email address.

Only emails matching the configured condition proceed to the next stage.

### 3. AI Response Generation

The Basic LLM Chain receives:

- Email subject
- Plain-text email content

It uses a professional assistant prompt to generate a polite response.

### 4. Groq Chat Model

The Groq Chat Model provides the language model used by the Basic LLM Chain.

**Model:** `llama-3.3-70b-versatile`

### 5. Automated Gmail Delivery

The Gmail node sends the AI-generated response using the configured destination address and a subject beginning with `Re:`.

**Important:** The current exported workflow uses a fixed sender condition and fixed Gmail destination. Configure these values according to your requirements before deployment. Dynamic replies to each original sender require additional workflow configuration.

---

## Technology Stack

| Technology      | Purpose                                   |
| --------------- | ----------------------------------------- |
| n8n             | Workflow automation                       |
| Gmail API       | Email monitoring and delivery             |
| Groq API        | AI model integration                      |
| Llama 3.3 70B   | Email response generation                 |
| Basic LLM Chain | Prompt processing and response generation |

## Repository Structure

```text
Gmail_response_n8n/
│
├── Gmail Auto-Responder.json
│   └── Importable n8n workflow
│
└── README.md
    └── Project documentation
```

## Installation & Setup

### Prerequisites

- An n8n instance (cloud or self-hosted).
- A Google Gmail account.
- Gmail OAuth2 credentials configured in n8n.
- A Groq API account.
- A Groq API key.

### Step 1: Clone the Repository

```bash
git clone https://github.com/KarthikeyanSA369/Gmail_response_n8n.git
```

```bash
cd Gmail_response_n8n
```

### Step 2: Open n8n

Start your n8n instance and open its workflow editor.

For a local n8n installation, the default address is:

```text
http://localhost:5678
```

### Step 3: Import the Workflow

1. Open the n8n editor.
2. Select the workflow import option.
3. Import `Gmail Auto-Responder.json`.
4. Open the imported workflow.
5. Review all nodes and connections.

### Step 4: Configure Gmail Credentials

1. Open the Gmail Trigger node.
2. Configure your Gmail OAuth2 credentials.
3. Open the Gmail Send Message node.
4. Connect your Gmail credentials.
5. Verify the required Gmail permissions.

### Step 5: Configure Groq API

1. Open the Groq Chat Model node.
2. Add your Groq API credentials.
3. Select the model:

```text
llama-3.3-70b-versatile
```

4. Save the configuration.

### Step 6: Customize Email Conditions

Before activating the workflow:

- Update the sender condition in the IF node.
- Update the destination address in the Gmail Send node.
- Review the AI response prompt.
- Verify the Gmail account and model credentials.

### Step 7: Test and Activate

1. Execute the workflow manually.
2. Send a test email matching your configured sender condition.
3. Check the AI-generated response.
4. Verify the configured Gmail destination.
5. Activate the workflow after successful testing.

---

## Example AI Prompt

The workflow uses a prompt similar to:

```text
You are a professional assistant.

Reply politely to this email.

Subject:
{{ $json.subject }}

Email:
{{ $json.textPlain }}

Generate only the reply.
```

This instructs the AI model to produce a polite, professional response based on the incoming email content.

## Configuration & Security

- Store Gmail OAuth2 credentials securely in n8n.
- Store Groq API keys in n8n credentials.
- Never publish API keys or OAuth tokens.
- Avoid exposing private email addresses in public workflow exports.
- Test with controlled email accounts before enabling automatic delivery.
- Review AI-generated responses for accuracy and inappropriate content.

## Current Project Scope

| Component               | Implementation |
| ----------------------- | -------------- |
| Gmail Trigger           | Implemented    |
| One-minute polling      | Configured     |
| Sender condition        | Implemented    |
| Basic LLM Chain         | Implemented    |
| Groq Chat Model         | Implemented    |
| Llama 3.3 70B           | Configured     |
| Gmail response delivery | Implemented    |

*The workflow represents the currently exported implementation. Additional features such as dynamic recipient replies, human approval, email classification, analytics and response history are not included in the exported workflow.*

## Future Enhancements

Potential improvements include:

- Dynamic replies to original senders.
- Human approval before sending responses.
- Email categorization and priority detection.
- Conversation context awareness.
- Response history and execution monitoring.
- Multiple sender rules.
- Error handling and retry mechanisms.

## Project Information

**Project:** Gmail AI Auto-Responder

**Category:** Artificial Intelligence & Workflow Automation

**Automation Platform:** n8n

**AI Provider:** Groq

**Language Model:** Llama 3.3 70B

**Email Integration:** Gmail

**Developer:** Karthikeyan S.A.

**GitHub Repository:**

[https://github.com/KarthikeyanSA369/Gmail_response_n8n](https://github.com/KarthikeyanSA369/Gmail_response_n8n)

---

\<p align="center">
&#x20; \<strong>Built with AI. Automated with n8n. Powered by Intelligence.\</strong>
\</p>
