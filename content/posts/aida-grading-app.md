---
title: "Building an AI Grading App with FastAPI"
date: 2026-04-27
categories: ["Projects", "School"]
tags: ["ai", "fastapi", "openai", "python", "claude", "pydantic", "prompt-engineering"]
canonicalURL: "https://ThorSchou.github.io/Portfolio/posts/aida-grading-app/"
---

For one of my AIDA (AI-drevne applikationer) assignments, I had to build a small
AI-driven application that evaluates student assignments using a custom rubric and
the OpenAI API. The app accepts an assignment submission, runs it through a structured
rubric, and returns detailed feedback — strengths, weaknesses, per-criterion scores,
and follow-up questions.

The whole thing was built with Claude Code, starting with Plan mode.

## The Assignment

The task was to integrate an LLM into a real backend — not just call the API and
print the response, but design proper prompts, define a rubric with proficiency levels,
and return structured JSON feedback that could actually be used. The focus was on
prompt engineering and LLM integration patterns rather than building something
production-ready.

## Using Plan Mode First

Before writing any code, I ran Claude Code in Plan mode and described what I needed.
It came back with a proposed tech stack: **FastAPI**, **Pydantic**, and **uvicorn**.

I hadn't used any of these before. FastAPI for the backend, Pydantic for defining
structured schemas for both the rubric and the LLM responses, and uvicorn as the
ASGI server. It also suggested separating concerns cleanly — `llm_client.py` for
the OpenAI calls, `prompts.py` for prompt templates, `rubric.py` for the criteria
logic, and `schemas.py` for the data models.

The plan made sense. I approved it and let Claude Code execute.

## What Got Built

The result is a Python backend with five endpoints:

- `GET /rubric` — returns the full grading rubric
- `GET /grades` — returns the grade scale
- `GET /samples/{student_id}` — serves example assignment submissions
- `POST /evaluate` — takes a submission, calls the OpenAI API, and returns structured feedback
- `GET /` — serves a simple HTML frontend to test it all

The feedback format includes an overall assessment, per-criterion scores with
explanations, identified strengths and weaknesses, and 4–6 follow-up questions
in JSON — exactly what the assignment required.

## It Worked on the First Try

The entire thing ran correctly the first time I started it. No debugging sessions,
no dependency issues, no broken endpoints. That was surprising — FastAPI and Pydantic
were both new to me, but the generated code was clean and the structure was solid.

## What I Took Away

Plan mode changes how you start a project. Instead of jumping straight into code,
you get a moment to see the full architecture before any files are created. When the
plan involves tools you don't know yet, you can ask questions or redirect — and then
let the agent handle the execution.

FastAPI and Pydantic turned out to be a great combination for this kind of LLM
integration. Pydantic makes it straightforward to define exactly what shape you
expect the LLM to return, which is one of the harder parts of prompt engineering
in practice.

The project is available on [GitHub](https://github.com/ThorSchou/AIDA).
