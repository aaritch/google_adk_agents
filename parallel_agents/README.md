# Parallel Workflows (Independent Researchers)

What if you have several tasks that are not dependent on each other? For example, researching three different topics. Running them in sequence can be slow and inefficient because each task waits for the previous one to finish.

## Concurrent Execution

When tasks are independent, you can run them concurrently using a `ParallelAgent`. A `ParallelAgent` executes all of its sub-agents at the same time, which can dramatically speed up the workflow. After all parallel tasks complete, you typically pass their combined results to a final aggregator step.

## When to use

- **Tasks are independent.**
- **Speed matters.**
- **Tasks can be executed concurrently.**

To learn more, see the official documentation for [parallel agents in ADK](https://google.github.io/adk-docs/agents/workflow-agents/parallel-agents/).

## Architecture — Multi-Topic Research

![Parallel agent architecture](images/parallel_agent.png)

### Example: Parallel Multi-Topic Research

- **Tech Researcher** — Researches AI/ML news and trends.
- **Health Researcher** — Researches recent medical and health news.
- **Finance Researcher** — Researches finance and fintech news and trends.
- **Aggregator Agent** — Combines all research findings into a single summary.

The research agents run in parallel (managed by a `ParallelAgent`). After they finish, an `AggregatorAgent` collects and consolidates the findings into one report. Often the `ParallelAgent` is nested within a `SequentialAgent` so you can run the parallel step as part of a larger sequential workflow.

---