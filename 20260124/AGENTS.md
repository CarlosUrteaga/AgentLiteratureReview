
# AGENTS.md

This document defines how AI agents (e.g., Codex CLI) must operate in this repository.

The repository is a **structured literature notebook**.  
Agents read papers (PDFs) and produce standardized analytical notes, then update the main index in `README.md`.

The agent MUST follow these rules strictly.

---

## 1. Repository Purpose

This repository stores analytical literature reviews related to:

- AI Agents
- Agent Architecture
- Agent Governance
- Agent Types and Contracts
- Evaluation and Observability
- Orchestration frameworks

Each paper processed becomes:

- One markdown file inside `notes/`
- One row added to the table in `README.md`

---

## 2. Directory Structure (strict)

```
root/
 ├── AGENTS.md
 ├── README.md        ← Main index (single source of truth)
 ├── notes/           ← All paper notes go here
 └── *.pdf            ← Input papers temporarily placed here
```

Agents MUST NOT create new folders.

---

## 3. Naming Convention for Notes

For a paper named:

```
2507.11277v1.pdf
```

The agent MUST create:

```
notes/2507.11277v1.md
```

Rules:
- Remove version suffix (v1, v2, etc.)
- Use only ASCII
- No spaces
- `.md` extension

---

## 4. Mandatory Output Template (for every note)

The agent MUST use EXACTLY this structure:

```markdown
# <Paper Title>

**Citation / Link:**  
**Authors:**  
**Year:**  

---

## 1. One-Line Contribution
<What is the core contribution in one sentence>

---

## 2. Problem the Paper Solves
<Clear explanation>

---

## 3. Proposed Solution / Architecture
<Detailed but structured explanation>

---

## 4. Key Concepts Introduced
- Concept 1
- Concept 2
- Concept 3

---

## 5. Relation to AI Agents / Agent Governance
<Why this matters for agent systems>

---

## 6. Strengths
- 
- 

---

## 7. Weaknesses
- 
- 

---

## 8. Ideas This Triggers for My Research
<Concrete ideas>

---

## 9. Tags
agent-types, orchestration, evaluation, governance, documentation
```

If information is missing, write `TBD`.  
The agent MUST NOT invent content.

---

## 5. Updating the Index (README.md)

After creating the note, the agent MUST update the table in `README.md`.

The agent MUST append one row to the table under **Índice de Revisión** with:

| ID | Title | Category | Relevancia Tesis |
|----|-------|----------|------------------|

Where:

- **ID** = paper numeric id (e.g., 2411.05285)
- **Title** = exact title from the paper
- **Category** = one of:

  - Documentation
  - Orchestration
  - Types
  - Evaluation
  - Governance

- **Relevancia Tesis** = Alta / Media / Baja

The agent MUST NOT modify previous rows.

---

## 6. Agent Procedure (deterministic steps)

When a PDF appears in root:

1. Read AGENTS.md
2. The agent MUST extract and read the textual content of the PDF.
   The PDF is the primary source of truth.
   The agent MUST parse the document and use its content to fill the template.
   Writing TBD is only allowed if the information truly does not appear in the paper.
3. Create `notes/<id>.md` using the template
4. Update `README.md` table
5. Stop

No extra commentary. No extra files.

---

## 7. Forbidden Actions

The agent MUST NOT:

- Create new folders
- Rename files
- Modify existing notes
- Change table structure in README
- Add explanations outside the template
