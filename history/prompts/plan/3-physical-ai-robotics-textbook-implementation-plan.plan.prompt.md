---id: 3
title: Physical AI Robotics Textbook Implementation Plan
stage: plan
date: 2025-12-06
surface: agent
model: claude-sonnet-4-5-20250929
feature: Physical-AI-Humanoid-Robotics-Textbook
branch: master
user: user
command: /sp.plan
labels: [plan]
links:
  spec: specs/Physical-AI-Humanoid-Robotics-Textbook/spec.md
  ticket: null
  adr: null
  pr: null
files:
  - specs/Physical-AI-Humanoid-Robotics-Textbook/plan.md
tests:
---

## Prompt

Goal:
Produce a fully functional Physical AI & Humanoid Robotics textbook using Claude Code + Spec-Kit Plus + Docusaurus, deploy it to GitHub Pages, and integrate an embedded RAG chatbot powered by OpenAI Agents, FastAPI, Neon, and Qdrant.

------------------------------------------------------------
1. System Architecture Overview
------------------------------------------------------------

The project has **three major systems**:

A. **Book Production System (Authoring Pipeline)**
   - Content created with Claude Code + Spec-Kit Plus prompts
   - All book chapters stored as Docusaurus Markdown
   - GitHub repository hosts the book + chatbot code
   - GitHub Actions builds the Docusaurus site automatically

B. **RAG Chatbot System**
   - Frontend: Chat widget embedded into the Docusaurus website
   - Backend: FastAPI server exposing chatbot + retrieval endpoints
   - Database Layer:
       - Postgres (Neon) stores metadata
       - Qdrant Cloud stores vector embeddings
   - OpenAI Agents handle:
       - Retrieval logic
       - Query answering using book content

C. **Deployment System**
   - Docusaurus static build → GitHub Pages
   - Chatbot FastAPI backend deployed on Render / Railway / Fly.io
   - Environment variables stored in GitHub Secrets

------------------------------------------------------------
2. Book Development Pipeline
------------------------------------------------------------

Phase 1: Constitution + Spec Creation
- Define /sp.constitution
- Define /sp.spec
- Define /sp.outline (chapter structure)
- Generate chapter prompts
- Validate APA citation standard

Phase 2: Chapter Production
- Each chapter written using Claude Code with:
  - Verified sources
  - APA citations
  - Diagrams (ASCII or Mermaid)
  - Code blocks for ROS 2, Isaac, Python, etc.
- Produce 5,000–7,000 total words

Phase 3: Docusaurus Integration
- Create Docusaurus project :   - Add chapters to `/docs` folder
- Configure sidebar in `sidebars.js`
- Implement PDF exporter

Phase 4: GitHub Pages Deployment
- Push to GitHub
- Enable Pages
- Add GitHub Actions workflow for auto-build

------------------------------------------------------------
3. RAG Chatbot Technical Plan
------------------------------------------------------------

A. Vectorization Pipeline
- Extract text from all Markdown files
- Chunk book into 300–500 token segments
- Generate embeddings using OpenAI Embeddings API
- Store vectors in Qdrant Cloud Collection:
- `id`
- `text_chunk`
- `embedding`
- `chapter`
- `section`

B. Metadata Storage (Neon Postgres)
- Store:
- Document titles
- Chapter mapping
- User selection references
- Interaction logs (optional)

C. Backend (FastAPI)
Endpoints:
- `/embed`: generate embeddings for new text
- `/query`: vector search in Qdrant
- `/ask`: OpenAI Agent handles:
- Retrieval
- Reasoning
- Citation output
- `/selection-query`: answer questions from user-selected text

Authentication:
- Bearer Token for API access
- Rate limiting

D. OpenAI Agent Logic
Agent Responsibilities:
- Accept user question
- Retrieve relevant text chunks
- Check grounding score
- Answer ONLY from retrieved book content
- Provide APA style citations

E. Frontend Chat Widget (Docusaurus)
- Insert a React-based chat component
- Connect to FastAPI backend using WebSocket or REST
- Support:
- Ask general question
- Select text → right-click → “Ask Chatbot”

------------------------------------------------------------
4. Course Content Integration Plan
------------------------------------------------------------

Each major module becomes a book chapter:

Chapter 1: Physical AI Foundations
Chapter 2: Embodied Intelligence & Humanoid Robotics
Chapter 3: Sensor Systems (LIDAR, Cameras, IMUs)
Chapter 4: ROS 2 Architecture
Chapter 5: URDF & Robot Kinematics
Chapter 6: Gazebo Simulation
Chapter 7: Unity High-Fidelity Rendering
Chapter 8: NVIDIA Isaac Sim
Chapter 9: Isaac ROS & Hardware Acceleration
Chapter 10: VSLAM & Navigation
Chapter 11: Vision-Language-Action Systems
Chapter 12: Conversational Robotics
Chapter 13: Capstone – Autonomous Humanoid

Each chapter will:
- Include diagrams & code examples
- Provide references to the hardware platforms
- Align learning outcomes with the course modules

------------------------------------------------------------
5. Hardware/Simulation Testing Plan
------------------------------------------------------------

Simulation Tools:
- NVIDIA Isaac Sim
- Gazebo
- Unity Engine

Hardware Platforms:
- NVIDIA Jetson Orin Nano/NX
- Intel RealSense D435i
- IMU modules
- ReSpeaker mic array
- Unitree Go2 / G1 robots (if available)

Testing Stages:
1. ROS 2 node testing on Ubuntu
2. Simulation testing in Gazebo
3. Perception pipeline testing in Isaac
4. VLA planning using LLMs
5. Deployment to Jetson Edge
6. Optional real robot deployment

------------------------------------------------------------
6. Development Timeline
------------------------------------------------------------

Week 1:
- Constitution / Spec-Kit setup
- Outline + initial chapters

Week 2–3:
- Complete all chapters (content generation)

Week 4:
- Docusaurus integration
- Build + GitHub Pages deployment

Week 5:
- RAG backend development (FastAPI + Qdrant + Neon)

Week 6:
- Chatbot frontend integration

Week 7:
- Full system testing (book + chatbot)
- Final polishing, PDF export

------------------------------------------------------------
7. Success Criteria Checklist
------------------------------------------------------------

Book:
✔ 5,000–7,000 words
✔ 15+ APA cited sources
✔ Zero plagiarism
✔ High academic clarity (grade 10–12 readability)
✔ Docusaurus build passes with no warnings

Chatbot:
✔ Retrieves only book content
✔ Accurate responses with citations
✔ Handles user-selected text queries
✔ Works inside the static site

Deployment:
✔ GitHub Pages deployment successful
✔ Backend hosted and connected
✔ All environment variables configured

------------------------------------------------------------
8. Risks & Mitigation
------------------------------------------------------------

Risk: GPU shortages for Isaac Sim
Mitigation: Use cloud-based NVIDIA Omniverse instances

Risk: Qdrant query latency
Mitigation: Use optimized embeddings + quantization

Risk: Docusaurus build failures
Mitigation: Use CI/CD GitHub Actions with caching

Risk: Chatbot hallucination
Mitigation: Strict retrieval-mode with grounding checks

## Response snapshot

I have successfully created the implementation plan for the "Physical AI & Humanoid Robotics Textbook" project at `specs/Physical-AI-Humanoid-Robotics-Textbook/plan.md`. I have also noted the following areas that require further clarification during the research phase:

*   Specific language/framework versions (e.g., Python, Node.js versions).
*   Performance goals (e.g., RAG chatbot response latency, Docusaurus build times).
*   Scale/scope (e.g., anticipated daily users for chatbot, content growth over time).

**Suggested commit message**:
```
docs: create implementation plan for Physical AI & Humanoid Robotics Textbook
```

## Outcome

- ✅ Impact: Implementation plan created and stored.
- 🧪 Tests: N/A
- 📁 Files: specs/Physical-AI-Humanoid-Robotics-Textbook/plan.md created.
- 🔁 Next prompts: The next step would be to conduct research for the identified clarifications.
- 🧠 Reflection: The shell script for PHR creation failed, necessitating agent-native file writing.

## Evaluation notes (flywheel)

- Failure modes observed: Shell script `.specify/scripts/bash/create-phr.sh` not found or executable.
- Graders run and results (PASS/FAIL): N/A
- Prompt variant (if applicable): N/A
- Next experiment (smallest change to try): Investigate the bash script path and permissions for future PHR creation attempts.
