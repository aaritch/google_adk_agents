# Sequential Workflows (The Assembly Line)

When tasks must run in a guaranteed, specific order, use a `SequentialAgent`. Think of it like an assembly line: each sub-agent runs in the order you list them, and the output of one agent becomes the input for the next. This creates a predictable, reliable workflow for pipelines where each step depends on the previous one.

## When to use

- **Order matters** and steps must run sequentially
- **Linear pipelines** where each step builds on prior outputs
- **Deterministic behavior** and simple error propagation

## Example Architecture — Blog Post Creation Pipeline

- ![Blog Post Pipeline Image]("images/sequential_agent.png")

This pipeline demonstrates a common sequential use case with three specialized agents:

- **Outline Agent** — creates a structured outline for a blog topic
- **Writer Agent** — expands the outline into a full blog post
- **Editor Agent** — revises the draft for clarity, flow, and style

Each agent receives the previous agent's output as input, so the Writer produces a draft the Editor improves.

## Notes and trade-offs

- Sequential workflows are ideal for dependent steps but can be slower when tasks are independent.
- If tasks are independent (for example, gathering research from different sources), consider using a `ParallelAgent` to run sub-agents concurrently and speed up execution.

## See also

- [ADK documentation](https://google.github.io/adk-docs/agents/workflow-agents/sequential-agents/) for `SequentialAgent` and `ParallelAgent` — consult your ADK docs for implementation details and examples.

---
