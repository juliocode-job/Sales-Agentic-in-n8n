# 🤖 Autonomous AI Sales Agent in n8n

### Low-Code Agentic Workflow for Intelligent Lead Outreach

This repository documents an autonomous AI sales agent built entirely on the n8n low-code platform. This project showcases how to orchestrate multiple AI models and APIs to create a sophisticated agent that can perceive, reason, and act on business data to drive sales growth.

---

## 1. The Business Problem
Sales teams often get bogged down by the slow, manual, and repetitive process of qualifying and contacting new leads. This leads to valuable time being spent on low-value tasks instead of actual conversations, and hot leads are often missed due to human delay. Standard automation also lacks the true personalization needed for high engagement.

## 2. The Solution: An Autonomous Agent
I designed and built an automated agentic workflow in n8n that works 24/7 to solve this problem. This agent autonomously handles the entire lead outreach process, from initial qualification and personalized emailing to analyzing responses and booking meetings directly on a calendar.

### Workflow Architecture
This diagram illustrates the four key phases of the agent's decision-making process.

```mermaid
graph TD
    subgraph "Phase 1: Intelligent Lead Qualification"
        A[Start: New Lead Data] --> B{1. OpenAI: Score Lead};
        B --> C{2. Filter: Hot Leads Only};
    end

    subgraph "Phase 2: Long-Term Memory (RAG)"
        C --> D[3. Create Embedding for Lead];
        D --> E["4. Query Supabase Vector DB <br> to find past interactions"];
    end

    subgraph "Phase 3: Personalized Action & Analysis"
        E --> F{"5. OpenAI: Generate Personalized <br> Outreach Message"};
        F --> G[6. Send Email via Gmail];
        G --> H(7. Wait and Listen for Reply);
        H --> I{"8. OpenAI: Analyze Reply Intent"};
    end

    subgraph "Phase 4: Autonomous Execution"
        I --> J{9. Is Reply Positive?};
        J -- Yes --> K["10a. Access Google Calendar <br> and Create Meeting"];
        J -- No --> L["10b. Log Lead in Google Sheet <br> for future follow-up"];
    end