---id: 2
title: Physical AI Robotics Textbook Feature Spec
stage: spec
date: 2025-12-06
surface: agent
model: claude-sonnet-4-5-20250929
feature: Physical-AI-Humanoid-Robotics-Textbook
branch: master
user: user
command: /sp.spec
labels: [spec]
links:
  spec: specs/Physical-AI-Humanoid-Robotics-Textbook/spec.md
  ticket: null
  adr: null
  pr: null
files:
  - specs/Physical-AI-Humanoid-Robotics-Textbook/spec.md
tests:
---

## Prompt

Title: Physical AI & Humanoid Robotics Textbook
Purpose: Produce a professionally structured, academically rigorous textbook covering Physical AI, embodied intelligence, humanoid robotics, ROS 2, Gazebo, Unity, NVIDIA Isaac, and Vision-Language-Action systems.

Primary Goal:
Create a complete book using Claude Code + Spec-Kit Plus + Docusaurus, deploy it on GitHub Pages, and integrate a RAG-based chatbot capable of answering questions from the book.

---

## Scope of Work

1. **Textbook Creation**
- 5,000–7,000 word textbook
- Covers Physical AI, embodied intelligence, humanoid control systems, ROS 2, Gazebo, Isaac Sim, VLA (Vision-Language-Action) systems
- Includes real-world examples, diagrams, definitions, workflows, and academic explanations
- Must be produced using Docusaurus and exported as a PDF with embedded APA citations

2. **RAG Chatbot Integration**
- Embed a Retrieval-Augmented Generation chatbot inside the published book
- Powered by:
  - OpenAI Agents / ChatKit SDKs
  - FastAPI backend
  - Neon Serverless Postgres (book metadata)
  - Qdrant Cloud (vector search)
- Chatbot must:
  - Answer questions **only** from book content
  - Answer questions based on **user-selected text**
  - Provide citations/reference mapping for answers

3. **Deployment Requirements**
- Deploy book to GitHub Pages using Docusaurus build
- Ensure RAG chatbot works inside the static site
- Validate build integrity (no broken links, missing images, or failed citations)

---

## Course Alignment

Textbook content must cover all core modules:

### Module 1 — The Robotic Nervous System (ROS 2)
- ROS 2 nodes, topics, services
- rclpy integration with AI agents
- URDF for humanoid robots
- Robot controllers & middleware principles

### Module 2 — The Digital Twin (Gazebo & Unity)
- Physics simulation (gravity, collisions)
- High-fidelity simulation in Unity
- Building digital environments
- Sensor simulation: LiDAR, RGB-D, IMU

### Module 3 — The AI-Robot Brain (NVIDIA Isaac)
- Isaac Sim for synthetic data
- Isaac ROS acceleration stack
- VSLAM, navigation pipelines
- Path planning for humanoid robots

### Module 4 — VLA (Vision-Language-Action Robotics)
- Whisper for voice commands
- LLM-based action decomposition
- Cognitive planning (“Clean the room” → ROS 2 action sequence)
- Multi-modal perception + task execution

### Capstone
Simulated humanoid robot that:
- Accepts voice commands
- Plans its own actions
- Navigates obstacles
- Recognizes objects
- Manipulates objects

---

## Hardware & Lab Specifications

### Minimum Student Workstation (Digital Twin Rig)
- **GPU:** RTX 4070 Ti (12GB VRAM) or higher
- **CPU:** Intel i7 / AMD Ryzen 9
- **RAM:** 32–64 GB DDR5
- **OS:** Ubuntu 22.04

### Edge Computing Kit (Physical AI Brain)
- NVIDIA Jetson Orin Nano (8GB) or Orin NX (16GB)
- Intel RealSense D435i camera
- IMU sensor module
- ReSpeaker USB mic array

### Robot Options
- **Budget:** Unitree Go2 Edu
- **Mid-range:** Robotis OP3
- **Premium:** Unitree G1 Humanoid
- **Alternative:** Hiwonder TonyPi (for basic kinematics study)

---

## Functional Requirements

### 1. Book Requirements
- APA citation format
- 50%+ peer-reviewed academic sources
- 15+ minimum references
- Clear, CS-level academic writing
- Include diagrams, examples, and terminology sections
- Pass plagiarism (0% tolerance)

### 2. RAG Chatbot Requirements
- Accept text selection as retrieval input
- Provide citation-linked answers
- Embed directly into Docusaurus layout
- Use Qdrant vector DB for embeddings
- Store metadata in Neon Postgres
- FastAPI backend serving agent endpoints

### 3. Deployment Requirements
- GitHub Pages auto-build action
- Static Docusaurus website
- RAG chatbot operational within site
- PDF export with embedded links + citations

---

## Deliverables

1. **Complete Book**
- 5k–7k word textbook
- PDF with APA citations
- Docusaurus Markdown source + GitHub deployment config

2. **RAG Chatbot**
- FastAPI backend
- Embedding + vector search pipeline
- Integration script for Docusaurus frontend

3. **Spec-Kit Deliverables**
- /sp.constitution
- /sp.spec (this document)
- /sp.outline (chapter blueprint)
- /sp.chapters (individual chapter prompts)
- /sp.tasks (project tasks)

---

## Success Criteria

- Book passes academic fact-checking
- Zero plagiarism
- APA citations validated
- Successful Docusaurus deployment
- Chatbot accurately answers book questions
- Chatbot retrieval works only from book content
- PDF exported with embedded citations

## Response snapshot

I have successfully created the feature specification for the "Physical AI & Humanoid Robotics Textbook" project at `specs/Physical-AI-Humanoid-Robotics-Textbook/spec.md`.

**Suggested commit message**:
```
docs: create feature spec for Physical AI & Humanoid Robotics Textbook
```

## Outcome

- ✅ Impact: Feature specification created and stored.
- 🧪 Tests: N/A
- 📁 Files: specs/Physical-AI-Humanoid-Robotics-Textbook/spec.md created.
- 🔁 Next prompts: The next step would typically be to create the outline or plan based on this spec.
- 🧠 Reflection: The shell script for PHR creation failed, necessitating agent-native file writing.

## Evaluation notes (flywheel)

- Failure modes observed: Shell script `.specify/scripts/bash/create-phr.sh` not found or executable.
- Graders run and results (PASS/FAIL): N/A
- Prompt variant (if applicable): N/A
- Next experiment (smallest change to try): Investigate the bash script path and permissions for future PHR creation attempts.
