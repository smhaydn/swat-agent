# SWAT-Agent Benchmark Suite

This directory contains a set of "regression tests" for the agent system. These prompts cover Frontend, Backend, Security, Performance, and Specification tasks.

## Why Benchmark?
To ensure that as we upgrade the agents (adding meta-agents, changing prompts), we don't regress on basic capabilities.

## Structure
- `prompts.json`: A list of 25+ prompts with expected agent assignments.
- `run_benchmarks.ts`: A script to execute these prompts (either via simulation or actual API if configured).

## How to Run
```bash
npx tsx scripts/run_benchmarks.ts
```

## Output
The runner will create a folder in `.task_runs/benchmarks/<timestamp>/` with results for each prompt.
