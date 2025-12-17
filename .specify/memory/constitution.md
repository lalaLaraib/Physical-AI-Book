<!--
Sync Impact Report:
Version change: 1.0.0 -> 2.0.0 (MAJOR: Significant update to principles, standards, constraints, and success criteria sections)
Modified principles:
  - Accuracy through Primary Source Verification -> Source-Verified Accuracy
  - Clarity for Academic, CS-Focused Audience -> Academic Clarity
  - Reproducibility -> Reproducibility
  - Rigor -> Scholarly Rigor
  - Compliance with Key Standards -> Key Standards (expanded and refined)
Added sections: Key Standards, Constraints, Success Criteria
Removed sections: None (template sections were filled more explicitly)
Templates requiring updates:
  - .specify/templates/plan-template.md: ✅ updated
  - .specify/templates/spec-template.md: ✅ updated
  - .specify/templates/tasks-template.md: ✅ updated
  - README.md: ⚠ pending (not accessible)
  - docs/quickstart.md: ⚠ pending (not accessible)
Follow-up TODOs: None
-->
# Physical AI & Humanoid Robotics Textbook Constitution

## Purpose
Establish the governing principles, quality standards, constraints, and success criteria for producing a scholarly, technically rigorous textbook on Physical AI and Humanoid Robotics using Spec-Kit Plus, Claude Code, Docusaurus, and a RAG-enabled backend.

## Core Principles

### Source-Verified Accuracy
All technical claims MUST be validated using authoritative, primary, or peer-reviewed sources.

### Academic Clarity
Writing MUST target a computer-science-trained audience with precise, conceptually clear explanations.

### Reproducibility
Every fact, algorithm, procedure, or dataset MUST be traceable, citable, and independently verifiable.

### Scholarly Rigor
Peer-reviewed research, scientific standards, and recognized robotics literature MUST form the foundation of all content.

## Key Standards

*   Every factual statement MUST be supported by a verifiable reference.
*   Citation style: APA 7th edition (inline + reference list).
*   Minimum 50% of references MUST be peer-reviewed research articles or academic sources.
*   Zero-tolerance plagiarism policy; all content MUST be original and pass final plagiarism checks.
*   Maintain Flesch-Kincaid readability level between grades 10–12.

## Constraints

*   Total word count: 5,000–7,000 words.
*   Minimum reference count: 15 high-credibility sources.
*   Output format: PDF with embedded (live) APA citations, generated from Docusaurus-compatible Markdown.
*   Tooling requirements:
    *   Authored using Claude Code + Spec-Kit Plus workflows.
    *   Implemented and rendered using Docusaurus.
    *   Deployed publicly using GitHub Pages.
*   RAG Integration Requirements:
    *   All book content MUST be structured for retrieval-augmented generation.
    *   Backend tech stack: OpenAI Agents SDK, FastAPI, Neon (Postgres), Qdrant (Vector DB).

## Success Criteria

*   All claims are traceable to valid, high-quality sources.
*   Final plagiarism score: 0%.
*   External fact-checking review passed.
*   RAG chatbot MUST answer queries accurately using ONLY the textbook content as ground truth.
*   Docusaurus site builds cleanly without warnings; GitHub Pages deployment succeeds.
*   PDF exports with correct formatting, embedded citations, and internal consistency.

## Governance

*   All content MUST adhere to the principles, standards, constraints, and success criteria defined in this constitution.
*   Amendments to this constitution require a formal review and approval process.
*   Compliance reviews will be conducted periodically to ensure adherence to all established guidelines.

**Version**: 2.0.0 | **Ratified**: 2025-12-06 | **Last Amended**: 2025-12-06
