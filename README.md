# Campus Assistant Bot

> **An intelligent, multilingual AI-powered campus information assistant that transforms how students interact with university services.**

---

[![Status](https://img.shields.io/badge/Status-Production%20Ready-success?style=for-the-badge)](https://github.com/Deepender25/Campus-Assistant-bot)
[![Platform](https://img.shields.io/badge/Platform-Web%20%7C%20Telegram-blue?style=for-the-badge)]()
[![AI](https://img.shields.io/badge/AI%20Engine-Google%20Gemini-orange?style=for-the-badge)]()
[![Languages](https://img.shields.io/badge/Languages-English%20%7C%20Hindi-purple?style=for-the-badge)]()

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [System Architecture](#system-architecture)
- [User Journey](#user-journey)
- [Use Cases](#use-cases)
- [Technology Highlights](#technology-highlights)
- [Multi-Platform Support](#multi-platform-support)
- [Admin Dashboard](#admin-dashboard)
- [Screenshots](#screenshots)
- [Roadmap](#roadmap)
- [Contact](#contact)

---

## Overview

**Campus Assistant Bot** is a comprehensive AI-powered solution designed to revolutionize campus information delivery. Built with cutting-edge technologies, it provides instant, accurate responses to student queries in multiple languages, available 24/7 across multiple platforms.

### The Problem We Solve

| Challenge | Our Solution |
|-----------|--------------|
| Long queues at information desks | Instant AI responses 24/7 |
| Language barriers for diverse students | Automatic multilingual support |
| Inconsistent information across channels | Single source of truth with knowledge base |
| Limited office hours | Round-the-clock availability |
| Repetitive queries consuming staff time | Automated handling of FAQs |

---

## Key Features

### Intelligent Conversation Engine

**Sample Conversation:**

```
Student: hi

Campus Assistant: Hello! Welcome to Gurugram University. We're delighted 
to have you join our vibrant academic community.

Student: what is the admission process

Campus Assistant: I apologize, but I do not have specific information 
regarding the admission process. To get the most accurate and up-to-date 
details, I recommend contacting the relevant campus admissions office 
directly.

Student: admission process kya h?

Campus Assistant: Ji haan, main aapko admission process ke baare mein 
detail mein bata sakta hun... Sabse accurate aur latest information ke 
liye, main aapko suggest karunga ki aap directly Campus Admissions Office 
se contact karein.
```

- **Context-Aware Responses**: Maintains conversation history for coherent multi-turn dialogues
- **Natural Language Understanding**: Processes queries in natural, conversational language
- **Smart Fallback**: Gracefully escalates to human support when needed

### Multilingual Support

```mermaid
flowchart LR
    A[User Query] --> B{Language Detection}
    B -->|English| C[English Processing]
    B -->|Hindi| D[Hindi Processing]
    C --> E[Generate Response]
    D --> E
    E --> F[Reply in Same Language]
```

- **Automatic Detection**: No manual language selection needed
- **Native Responses**: Replies in the user's preferred language
- **Extensible**: Architecture supports adding new languages

### Dynamic Knowledge Base

- **PDF Document Processing**: Upload campus documents and FAQs
- **Vector Search**: Fast, semantic search across all documents
- **Real-time Updates**: Knowledge base can be updated without downtime
- **Source Attribution**: Know where each answer comes from

### Secure Admin Dashboard

- **Role-Based Access Control**: Administrator and Moderator roles
- **Analytics Dashboard**: Track usage patterns and popular queries
- **User Management**: Manage access and permissions
- **Document Management**: Upload, organize, and maintain knowledge base

---

## System Architecture

### High-Level Architecture

```mermaid
flowchart TB
    subgraph Clients["Client Applications"]
        WEB[Web Application]
        TG[Telegram Bot]
        FUTURE[Future: Mobile App]
    end

    subgraph Gateway["API Gateway Layer"]
        AUTH[Authentication]
        RATE[Rate Limiting]
    end

    subgraph Core["Core Services"]
        API[REST API]
        AI[AI Engine]
        KB[Knowledge Base]
    end

    subgraph Data["Data Layer"]
        VDB[(Vector Database)]
        RDB[(Relational Database)]
        CACHE[(Cache Layer)]
    end

    subgraph External["External Services"]
        GEMINI[Google Gemini AI]
        SUPABASE[Supabase Cloud]
    end

    WEB --> Gateway
    TG --> Gateway
    FUTURE --> Gateway
    
    Gateway --> Core
    
    API --> Data
    AI --> GEMINI
    KB --> VDB
    
    RDB --> SUPABASE
```

### Request Flow

```mermaid
sequenceDiagram
    participant U as User
    participant C as Client App
    participant A as API Server
    participant K as Knowledge Base
    participant AI as AI Engine
    
    U->>C: Sends Query
    C->>A: API Request
    A->>A: Detect Language
    A->>K: Search Relevant Context
    K-->>A: Return Context
    A->>AI: Query + Context
    AI-->>A: Generated Response
    A->>A: Log Conversation
    A-->>C: JSON Response
    C-->>U: Display Answer
```

---

## User Journey

### Student Experience

```mermaid
journey
    title Student Query Journey
    section Discovery
      Opens chatbot: 5: Student
      Sees welcome message: 5: System
    section Interaction
      Types question: 5: Student
      Processes query: 5: System
      Receives answer: 5: Student
    section Resolution
      Gets helpful response: 5: Student
      Continues conversation: 4: Student
      Query resolved: 5: System
```

### Administrator Experience

```mermaid
journey
    title Admin Management Journey
    section Login
      Accesses dashboard: 5: Admin
      Authenticates: 5: System
    section Management
      Views analytics: 5: Admin
      Uploads documents: 5: Admin
      Manages users: 5: Admin
    section Monitoring
      Reviews conversations: 4: Admin
      Identifies improvements: 4: Admin
```

---

## Use Cases

### For Students

| Query Category | Example Questions |
|----------------|-------------------|
| **Admissions** | "What documents are needed for admission?" |
| **Fees & Payments** | "What is the fee structure for B.Tech?" |
| **Academic Calendar** | "When do exams start?" |
| **Campus Facilities** | "Where is the library located?" |
| **Contact Info** | "How can I reach the registrar office?" |

### For Administrators

| Feature | Benefit |
|---------|---------|
| **Analytics Dashboard** | Track most-asked questions, identify gaps |
| **Knowledge Base Management** | Keep information up-to-date |
| **User Management** | Control access to sensitive features |
| **Conversation Logs** | Quality assurance and improvement |

### For Institutions

| Benefit | Impact |
|---------|--------|
| **Reduced Staff Load** | Free up staff for complex queries |
| **24/7 Availability** | Support students anytime |
| **Consistent Information** | Single source of truth |
| **Multilingual Reach** | Serve diverse student population |

---

## Technology Highlights

### AI & Machine Learning

| Component | Technology | Purpose |
|-----------|------------|---------|
| **LLM** | Google Gemini 1.5 | Natural language understanding & generation |
| **Embeddings** | Vector Embeddings | Semantic document search |
| **RAG** | Retrieval-Augmented Generation | Context-aware responses |

### Modern Tech Stack

```mermaid
flowchart LR
    subgraph Frontend
        NEXT[Next.js 14]
        REACT[React 18]
        TW[Tailwind CSS]
    end
    
    subgraph Backend
        FLASK[Flask]
        PYTHON[Python 3.11+]
    end
    
    subgraph Database
        SUPA[Supabase]
        CHROMA[ChromaDB]
    end
    
    subgraph AI
        GEMINI[Google Gemini]
        LANGCHAIN[LangChain]
    end
```

### Security Features

- **JWT Authentication** with secure token refresh
- **Role-Based Access Control** (RBAC)
- **Secure Session Management**
- **Audit Logging** for all admin actions
- **Environment-based Configuration**

---

## Multi-Platform Support

### Web Application

- Responsive design for all devices
- Modern, intuitive chat interface
- Real-time message updates
- Dark/Light theme support

### Telegram Bot

- Native Telegram integration
- Inline buttons for quick actions
- Image processing support
- Seamless conversation experience

### Future Platforms

- **Mobile App** (iOS & Android)
- **WhatsApp Integration**
- **Voice Assistant Support**

---

## Admin Dashboard

### Login Screen

<p align="center">
  <img width="1919" height="999" alt="login" src="https://github.com/user-attachments/assets/f3fef6d3-2802-48f3-a3a6-ae2284220f5d" />
</p>

### Dashboard Overview

<p align="center">
  <img width="1919" height="992" alt="dashboard" src="https://github.com/user-attachments/assets/7d8a1c3c-4454-4a4c-ad0c-588bca8fa84f" />
</p>

### Key Modules

```mermaid
flowchart TB
    subgraph Dashboard["Admin Dashboard"]
        HOME[Overview]
        CONV[Conversations]
        KB[Knowledge Base]
        UPLOAD[Document Upload]
        ANALYTICS[Analytics]
        USERS[User Management]
        SETTINGS[Settings]
    end
```

| Module | Description |
|--------|-------------|
| **Overview** | Quick stats, recent activity, system health |
| **Conversations** | Browse and search conversation history |
| **Knowledge Base** | View and manage indexed documents |
| **Document Upload** | Add new PDFs to the knowledge base |
| **Analytics** | Usage metrics, popular queries, trends |
| **User Management** | Manage admin and moderator accounts |
| **Settings** | Configure system behavior and responses |

---

## Screenshots

### Conversations
<p align="center">
  <img width="1918" height="983" alt="conversations" src="https://github.com/user-attachments/assets/dcac1b08-7948-44a6-9277-8942bffdaeca" />
</p>

### Knowledge Base
<p align="center">
  <img width="1919" height="997" alt="knowledge-base" src="https://github.com/user-attachments/assets/59793fdf-e837-4b62-aee5-80bbe7afaa11" />
</p>

### Document Upload
<p align="center">
  <img width="1919" height="985" alt="document-upload" src="https://github.com/user-attachments/assets/e50abbab-3211-4344-8028-0521739a67ac" />
</p>

### Analytics
<p align="center">
  <img width="1919" height="987" alt="analytics" src="https://github.com/user-attachments/assets/282b2818-429f-4a60-90e8-168bba826249" />
</p>

### User Management
<p align="center">
  <img width="1919" height="997" alt="user-management" src="https://github.com/user-attachments/assets/fff6c86f-86fc-4dfb-a05e-159fe3d1174d" />
</p>

---

## Roadmap

### Current Version (v1.0)

- [x] Web chat interface
- [x] Telegram bot integration
- [x] English & Hindi support
- [x] PDF document processing
- [x] Admin dashboard
- [x] User authentication
- [x] Analytics & logging

### Upcoming Features

```mermaid
timeline
    title Development Roadmap
    Q1 2026 : Voice Input/Output
           : WhatsApp Integration
           : Mobile App (Beta)
    Q2 2026 : Additional Languages
           : Advanced Analytics
           : API for Third-party Integration
    Q3 2026 : Voice Assistant Support
           : Campus System Integration
           : Multi-tenant Architecture
    Q4 2026 : AI Model Fine-tuning
           : Predictive Analytics
           : Enterprise Features
```

### Feature Requests

We're always looking to improve! Planned enhancements include:

- Voice input and text-to-speech output
- Native mobile applications
- Support for regional Indian languages
- Advanced predictive analytics
- Integration with campus ERP systems
- WhatsApp Business integration

---

## Contact

### Project Maintainer

**Deepender Yadav**

[![GitHub](https://img.shields.io/badge/GitHub-Deepender25-181717?style=for-the-badge&logo=github)](https://github.com/Deepender25)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/deepender25)
[![Email](https://img.shields.io/badge/Email-Contact-D14836?style=for-the-badge&logo=gmail)](mailto:yadavdeepender65@gmail.com)

### For Business Inquiries

Interested in implementing Campus Assistant Bot for your institution?

- **Email**: yadavdeepender65@gmail.com
- **Portfolio**: https://deependerportfolio.vercel.app

---

## License

This is a **proprietary, closed-source project**. All rights reserved.

Unauthorized copying, modification, distribution, or use of this software, via any medium, is strictly prohibited without explicit written permission from the author.

---

<p align="center">
  <strong>Built with passion for better campus experiences</strong>
</p>

<p align="center">
  <sub>© 2025-2026 Deepender Yadav. All Rights Reserved.</sub>
</p>
