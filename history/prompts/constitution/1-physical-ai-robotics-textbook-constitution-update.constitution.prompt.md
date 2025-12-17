--- id: 1
title: Physical AI Robotics Textbook Constitution Update
stage: constitution
date: 2025-12-06
surface: agent
model: claude-sonnet-4-5-20250929
feature: none
branch: master
user: user
command: /sp.constitution
labels: [constitution]
links:
  spec: null
  ticket: null
  adr: null
  pr: null
files:
  - ./.specify/memory/constitution.md
tests:
---

## Prompt

project: Physical AI & Humanoid Robotics Textbook

Purpose:
Establish the governing principles, quality standards, constraints, and success criteria for producing a scholarly, technically rigorous textbook on Physical AI and Humanoid Robotics using Spec-Kit Plus, Claude Code, Docusaurus, and a RAG-enabled backend.

-------------------------------------------------------------------------------
CORE PRINCIPLES
-------------------------------------------------------------------------------
- Source-Verified Accuracy: All technical claims must be validated using
  authoritative, primary, or peer-reviewed sources.
- Academic Clarity: Writing must target a computer-science-trained audience with
  precise, conceptually clear explanations.
- Reproducibility: Every fact, algorithm, procedure, or dataset must be
  traceable, citable, and independently verifiable.
- Scholarly Rigor: Peer-reviewed research, scientific standards, and recognized
  robotics literature must form the foundation of all content.

-------------------------------------------------------------------------------
KEY STANDARDS
-------------------------------------------------------------------------------
- Every factual statement must be supported by a verifiable reference.
- Citation style: APA 7th edition (inline + reference list).
- Minimum 50% of references must be peer-reviewed research articles or academic
  sources.
- Zero-tolerance plagiarism policy; all content must be original and pass final
  plagiarism checks.
- Maintain Flesch-Kincaid readability level between grades 10–12.

-------------------------------------------------------------------------------
CONSTRAINTS
-------------------------------------------------------------------------------
- Total word count: 5,000–7,000 words.
- Minimum reference count: 15 high-credibility sources.
- Output format: PDF with embedded (live) APA citations, generated from
  Docusaurus-compatible Markdown.
- Tooling requirements:
  * Authored using Claude Code + Spec-Kit Plus workflows.
  * Implemented and rendered using Docusaurus.
  * Deployed publicly using GitHub Pages.
- RAG Integration Requirements:
  * All book content must be structured for retrieval-augmented generation.
  * Backend tech stack: OpenAI Agents SDK, FastAPI, Neon (Postgres), Qdrant
    (Vector DB).

-------------------------------------------------------------------------------
SUCCESS CRITERIA
-------------------------------------------------------------------------------
- All claims are traceable to valid, high-quality sources.
- Final plagiarism score: 0%.
- External fact-checking review passed.
- RAG chatbot must answer queries accurately using ONLY the textbook content as
  ground truth.
- Docusaurus site builds cleanly without warnings; GitHub Pages deployment
  succeeds.
- PDF exports with correct formatting, embedded citations, and internal
  consistency.

## Response snapshot

I have successfully updated the project constitution.

**New Constitution Version**: 2.0.0 (MAJOR: Significant update to principles, standards, constraints, and success criteria sections)
**Files flagged for manual follow-up**:
*   `README.md`: ⚠ pending (not accessible, may require updates for new principles/standards)
*   `docs/quickstart.md`: ⚠ pending (not accessible, may require updates for new principles/standards)

**Suggested commit message**:
```
docs: amend constitution to v2.0.0 (significant update)
```

## Outcome

- ✅ Impact: Constitution updated with detailed principles, standards, constraints, and success criteria.
- 🧪 Tests: No explicit tests run for constitution update.
- 📁 Files: ./.specify/memory/constitution.md updated.
- 🔁 Next prompts: Continue with project development based on the updated constitution.
- 🧠 Reflection: The shell script for PHR creation failed, necessitating agent-native file writing.

## Evaluation notes (flywheel)

- Failure modes observed: Shell script `.specify/scripts/bash/create-phr.sh` not found or executable.
- Graders run and results (PASS/FAIL): N/A
- Prompt variant (if applicable): N/A
- Next experiment (smallest change to try): Investigate the bash script path and permissions for future PHR creation attempts.
