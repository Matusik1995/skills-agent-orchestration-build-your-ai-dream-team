# Agent team

Mona's Project Pulse dashboard will be built with a small custom agent team in GitHub Copilot CLI inside the Codespace. The team is defined under `.github/agents/` and coordinated by the Orchestrator so work stays scoped, parallelized when possible, and validated before handoff.

- Orchestrator — `Claude Opus 4.7` — coordinates the overall workflow, breaks the work into phases, delegates tasks to the specialist agents, and verifies the final dashboard outcome. Source: `.github/agents/orchestrator.agent.md`.
- Planner — `Claude Opus 4.7` — researches the repository, identifies dependencies and edge cases, and creates the implementation plan for the Project Pulse dashboard. Source: `.github/agents/planner.agent.md`.
- Designer — `Gemini 3.1 Pro` — focuses on the Project Pulse experience: dashboard layout, hierarchy, accessibility, styling, and responsive presentation. Source: `.github/agents/designer.agent.md`.
- Coder — `GPT-5.5` — implements the actual static dashboard, project data, styling, and any required runnable app support such as `.vscode/launch.json` for the "Run Project Pulse Dashboard" preview. Source: `.github/agents/coder.agent.md`.

How the team works together:
1. The Orchestrator asks the Planner to map the work and produce the implementation plan.
2. The Designer shapes the dashboard UX and visual direction for the Project Pulse frontend.
3. The Coder builds the app files and launch configuration so the dashboard can run in the browser.
4. The Orchestrator reviews the result, checks the app and validation expectations, and reports the final handoff.

This keeps the work aligned with the exercise goals: planning, design, implementation, and validation for Mona's Project Pulse dashboard.
