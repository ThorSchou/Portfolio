---
title: "Building a RAG Chatbot for My Portfolio"
date: 2026-04-17
categories: ["Projects", "Tutorials"]
tags: ["ai", "rag", "dify", "openai", "chatbot", "github-actions"]
canonicalURL: "https://ThorSchou.github.io/Portfolio/posts/rag-chatbot/"
---

One of the coolest features on this portfolio is the AI chatbot in the bottom right corner.
It's not just a regular chatbot — it uses RAG (Retrieval-Augmented Generation) to answer
questions specifically about me, my projects and my posts.

## What is RAG?

RAG stands for Retrieval-Augmented Generation. Instead of relying solely on what an AI
model already knows, RAG lets the model search through a knowledge base of your own
documents before answering. This means the bot can answer questions about my specific
projects and experience rather than making things up.

## The Stack

- **Dify** — an open-source platform for building AI-powered apps
- **OpenAI gpt-4o-mini** — the language model powering the responses
- **GitHub Actions** — automatically syncs new posts to the knowledge base
- **Hugo** — the static site generator serving the portfolio

## How It Works

1. I write a new blog post in markdown and push it to GitHub
2. A GitHub Action automatically uploads the markdown file to Dify's knowledge base
3. If the file already exists, it deletes the old version first to avoid duplicates
4. The chatbot can now answer questions about the new post
5. Each post includes a canonical URL so the bot can link directly to it

## Setting It Up

The chatbot is embedded into the Hugo site using a single script in
`layouts/partials/extend-footer.html`. Dify provides this embed script after you
publish your chatbot app.

The auto-sync workflow lives in `.github/workflows/sync-dify.yml` and triggers
on every push that changes files in the `content/` folder.

## What I Learned

Building this taught me how RAG works in practice — how documents get chunked,
embedded as vectors, and retrieved based on semantic similarity to a user's query.
It also showed me how powerful GitHub Actions can be for automating workflows beyond
just deployment.
