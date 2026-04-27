---
title: "Using Coding Agents in My Workflow"
date: 2026-04-27
categories: ["Projects", "Learning"]
tags: ["ai", "coding-agents", "claude", "productivity", "tools"]
canonicalURL: "https://ThorSchou.github.io/Portfolio/posts/coding-agents/"
---

Coding agents have become a regular part of how I build things — and this portfolio
is a good example. A lot of the setup, automation, and content here was built
with the help of AI coding agents.

## What Is a Coding Agent?

A coding agent is more than a code autocomplete tool. Instead of just suggesting
the next line, an agent can take a task, read through your codebase, make changes
across multiple files, run commands, and iterate until the task is done.

The key difference from a regular AI assistant is **autonomy**. You describe what
you want, and the agent figures out the steps — reading files, writing code, and
fixing its own mistakes along the way.

## How I Use Them

My main tool is **Claude Code**, which runs directly in the terminal and has access
to my project files. I use it for:

- Setting up new features from scratch (like the Dify RAG sync workflow)
- Writing GitHub Actions workflows I've never written before
- Debugging configuration issues where I'm not sure what's wrong
- Generating first drafts of blog posts and refining them together

The workflow feels like pair programming. I describe the goal, the agent proposes
an approach, I approve or redirect, and it executes.

## What Actually Works Well

The biggest win is **crossing unfamiliar territory faster**. As a student, I often
need to work with tools I've never used before. An agent lets me get something
working first and understand it second — which turns out to be a great way to learn.

It's also good at tasks that are tedious but not creative — boilerplate, config
files, repetitive edits across files. Things I could do myself but would rather not.

## What Doesn't Work

Agents struggle when the goal is vague. If I say "make the site look better",
that goes nowhere useful. The more specific and concrete the task, the better the result.

They also can't tell if something *feels* right — a layout change might be
technically correct but visually off. For anything UI-related, I still have to
check it myself.

## What I Learned

Using coding agents has made me better at breaking work into clear, concrete tasks.
That skill turns out to be useful whether you're talking to an AI or a teammate.
The agent forces you to be precise about what you actually want — which is a
surprisingly good habit to build.
