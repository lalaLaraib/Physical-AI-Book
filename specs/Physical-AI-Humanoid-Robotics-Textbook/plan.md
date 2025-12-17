# Implementation Plan: Physical AI & Humanoid Robotics Textbook

**Branch**: `feature/ai-robotics-textbook` | **Date**: 2025-12-06 | **Spec**: /specs/Physical-AI-Humanoid-Robotics-Textbook/spec.md
**Input**: Feature specification from `/specs/Physical-AI-Humanoid-Robotics-Textbook/spec.md`

**Note**: This template is filled in by the `/sp.plan` command. See `.specify/templates/commands/plan.md` for the execution workflow.

## Summary

Produce a fully functional Physical AI & Humanoid Robotics textbook using Claude Code + Spec-Kit Plus + Docusaurus, deploy it to GitHub Pages, and integrate an embedded RAG chatbot powered by OpenAI Agents, FastAPI, Neon, and Qdrant.

## Technical Context

**Language/Version**: Python (for FastAPI backend, OpenAI Agents), JavaScript/TypeScript (for Docusaurus frontend, React chat widget). Specific versions: NEEDS CLARIFICATION (e.g., Python 3.11+, Node.js 18+)
**Primary Dependencies**: OpenAI Agents SDK, FastAPI, Neon Serverless Postgres, Qdrant Cloud, Docusaurus, React.
**Storage**: Neon Serverless Postgres (metadata), Qdrant Cloud (vector embeddings).
**Testing**: Docusaurus build validation (broken links, images, citations), RAG chatbot accuracy, retrieval efficacy, citation mapping.
**Target Platform**: GitHub Pages (Docusaurus static site), Render/Railway/Fly.io (FastAPI backend).
**Project Type**: Web application (static frontend + API backend).
**Performance Goals**: NEEDS CLARIFICATION (e.g., RAG chatbot response latency, Docusaurus build times).
**Constraints**: Total word count: 5,000–7,000 words. Minimum reference count: 15 high-credibility sources. Output format: PDF with embedded APA citations from Docusaurus Markdown. Tooling: Authored with Claude Code + Spec-Kit Plus, rendered with Docusaurus, deployed to GitHub Pages. RAG Integration: All book content structured for RAG, Backend tech stack: OpenAI Agents SDK, FastAPI, Neon (Postgres), Qdrant (Vector DB).
**Scale/Scope**: NEEDS CLARIFICATION (e.g., anticipated daily users for chatbot, content growth over time).

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

*   **Source-Verified Accuracy**: All technical claims in the textbook MUST be validated using authoritative, primary, or peer-reviewed sources. (Passed - explicitly stated in plan and success criteria)
*   **Academic Clarity**: Writing MUST target a computer-science-trained audience with precise, conceptually clear explanations. (Passed - explicitly stated in plan and success criteria)
*   **Reproducibility**: Every fact, algorithm, procedure, or dataset MUST be traceable, citable, and independently verifiable. (Passed - explicitly stated in plan and success criteria)
*   **Scholarly Rigor**: Peer-reviewed research, scientific standards, and recognized robotics literature MUST form the foundation of all content. (Passed - explicitly stated in plan and success criteria)
*   **Key Standards Compliance**: Adherence to APA 7th, 50%+ peer-reviewed articles, 15+ references, zero-tolerance plagiarism, Flesch-Kincaid 10–12. (Passed - explicitly stated in plan and success criteria)
*   **Constraints Compliance**: Word count, reference count, PDF output, Docusaurus/Claude Code/Spec-Kit Plus tooling, RAG integration with specified stack. (Passed - all constraints are clearly defined and addressed in the plan).
*   **Success Criteria Alignment**: Book passes fact-checking, zero plagiarism, APA validated, Docusaurus deployment, accurate RAG chatbot from book content, PDF export. (Passed - all success criteria from the constitution are explicitly covered in the plan's success criteria checklist).

## Project Structure

### Documentation (this feature)

```text
specs/Physical-AI-Humanoid-Robotics-Textbook/
├── plan.md              # This file (/sp.plan command output)
├── research.md          # Phase 0 output (/sp.plan command)
├── data-model.md        # Phase 1 output (/sp.plan command)
├── quickstart.md        # Phase 1 output (/sp.plan command)
├── contracts/           # Phase 1 output (/sp.plan command)
└── tasks.md             # Phase 2 output (/sp.tasks command - NOT created by /sp.plan)
```

### Source Code (repository root)

```text
.github/workflows/        # GitHub Actions for Docusaurus build & deploy
book/
├── docs/                 # Docusaurus Markdown chapters
│   ├── chapter1.md
│   └── ...
├── src/                  # Docusaurus custom components (e.g., chat widget)
├── docusaurus.config.js
└── sidebars.js

rag-chatbot/
├── backend/
│   ├── app/              # FastAPI application
│   ├── core/             # OpenAI Agent logic, retrieval
│   ├── database/         # Neon Postgres client, Qdrant client
│   └── requirements.txt
└── frontend/             # React chat widget (integrated into Docusaurus src/)

```

**Structure Decision**: The project will adopt a multi-project structure: a `book/` directory for the Docusaurus site and a `rag-chatbot/` directory for the backend, with the chatbot frontend integrated into the Docusaurus `src/`. GitHub Actions workflows will manage the build and deployment for both systems.

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| N/A | N/A | N/A |

## System Architecture Overview

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

## Book Development Pipeline

**Phase 1: Constitution + Spec Creation**
- Define /sp.constitution
- Define /sp.spec
- Define /sp.outline (chapter structure)
- Generate chapter prompts
- Validate APA citation standard

**Phase 2: Chapter Production**
- Each chapter written using Claude Code with:
  - Verified sources
  - APA citations
  - Diagrams (ASCII or Mermaid)
  - Code blocks for ROS 2, Isaac, Python, etc.
- Produce 5,000–7,000 total words

**Phase 3: Docusaurus Integration**
- Create Docusaurus project
- Add chapters to `/docs` folder
- Configure sidebar in `sidebars.js`
- Implement PDF exporter

**Phase 4: GitHub Pages Deployment**
- Push to GitHub
- Enable Pages
- Add GitHub Actions workflow for auto-build

## RAG Chatbot Technical Plan

A. **Vectorization Pipeline**
- Extract text from all Markdown files
- Chunk book into 300–500 token segments
- Generate embeddings using OpenAI Embeddings API
- Store vectors in Qdrant Cloud Collection:
  - `id`
  - `text_chunk`
  - `embedding`
  - `chapter`
  - `section`

B. **Metadata Storage (Neon Postgres)**
- Store:
  - Document titles
  - Chapter mapping
  - User selection references
  - Interaction logs (optional)

C. **Backend (FastAPI)**
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

D. **OpenAI Agent Logic**
Agent Responsibilities:
- Accept user question
- Retrieve relevant text chunks
- Check grounding score
- Answer ONLY from retrieved book content
- Provide APA style citations

E. **Frontend Chat Widget (Docusaurus)**
- Insert a React-based chat component
- Connect to FastAPI backend using WebSocket or REST
- Support:
  - Ask general question
  - Select text → right-click → “Ask Chatbot”

## Course Content Integration Plan

Each major module becomes a book chapter:

*   Chapter 1: Physical AI Foundations
*   Chapter 2: Embodied Intelligence & Humanoid Robotics
*   Chapter 3: Sensor Systems (LIDAR, Cameras, IMUs)
*   Chapter 4: ROS 2 Architecture
*   Chapter 5: URDF & Robot Kinematics
*   Chapter 6: Gazebo Simulation
*   Chapter 7: Unity High-Fidelity Rendering
*   Chapter 8: NVIDIA Isaac Sim
*   Chapter 9: Isaac ROS & Hardware Acceleration
*   Chapter 10: VSLAM & Navigation
*   Chapter 11: Vision-Language-Action Systems
*   Chapter 12: Conversational Robotics
*   Chapter 13: Capstone – Autonomous Humanoid

Each chapter will:
- Include diagrams & code examples
- Provide references to the hardware platforms
- Align learning outcomes with the course modules

## Hardware/Simulation Testing Plan

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

## Success Criteria Checklist

**Book**:
✔ 5,000–7,000 words
✔ 15+ APA cited sources
✔ Zero plagiarism
✔ High academic clarity (grade 10–12 readability)
✔ Docusaurus build passes with no warnings

**Chatbot**:
✔ Retrieves only book content
✔ Accurate responses with citations
✔ Handles user-selected text queries
✔ Works inside the static site

**Deployment**:
✔ GitHub Pages deployment successful
✔ Backend hosted and connected
✔ All environment variables configured

## Risks & Mitigation

**Risk**: GPU shortages for Isaac Sim
Mitigation: Use cloud-based NVIDIA Omniverse instances

**Risk**: Qdrant query latency
Mitigation: Use optimized embeddings + quantization

**Risk**: Docusaurus build failures
Mitigation: Use CI/CD GitHub Actions with caching

**Risk**: Chatbot hallucination
Mitigation: Strict retrieval-mode with grounding checks

## Development Timeline

*This section is intentionally excluded as per instructions to avoid providing time estimates in planning tasks.*
