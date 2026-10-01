# e-tutorAI: Multi-Agent Adaptive Tutoring System

e-Tutor AI is a multi-Agent AI that works as an adaptive Tutoring Team for Python Programming for Beginners. It is built on n8n assistant.  

## 1. Chosen Use Case & Rationale
**Use Case:** A beginner-friendly Python tutoring system that adapts to each student.

**Rationale:** A single AI agent struggles to plan lessons, explain ideas, and create quizzes all at once. It often makes up facts or gives answers that are too hard to understand. By splitting the work among a Supervisor and three Specialists, each agent stays focused and gives better answers. The Explainer agent also uses Wikipedia to check facts before teaching.

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

# Reflection
What advantages did the multi-agent approach provide vs. a hypothetical single agent?
The main advantage of a multi-agent system is specialization. A single agent struggles to be a teacher, planner, and quiz maker all at once. Splitting the roles ensures each agent gives high-quality, focused answers.
This approach also makes the system easier to scale and debug. Adding a new specialist, like a Code Reviewer, does not break the existing agents. You just add a new node and update the Supervisor's routing rules.
Finally, multi-agent systems improve safety and reduce costs. The Supervisor can catch sensitive topics and route them to a human if needed. Also, you only use expensive AI models for the specific specialist that is actually required.
