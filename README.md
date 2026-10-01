# e-tutorAI: Multi-Agent Adaptive Tutoring System

## 1. Chosen Use Case & Rationale
**Use Case:** Adaptive Python Programming Tutoring for Beginners.
**Rationale:** A single monolithic LLM often struggles to balance the distinct pedagogical tasks of curriculum design, empathetic explanation, and rigorous assessment. It tends to hallucinate facts or provide overly complex answers. By splitting the task into a **Supervisor** and three **Specialist Agents** (Curriculum, Explainer, Quiz), we ensure each agent has a focused system prompt, reducing hallucinations and improving pedagogical quality. The Explainer agent is also equipped with a Wikipedia tool to ground its explanations in factual data.

## 2. Agent Team Diagram & Communication Flow
```text
[User Chat Input]
       │
       ▼
[ Tutor Supervisor ] (LLM + Structured Output Parser + Memory)
       │
       │ (Routes based on intent)
       ▼
[ Route to Specialist (Switch) ]
       ├───► [ Curriculum Planner ] (LLM: Designs learning path)
       ├───► [ Concept Explainer ] (LLM + Wikipedia Tool: Teaches concepts)
       └───► [ Quiz Generator ] (LLM: Creates assessments)
