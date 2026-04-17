---
title: "Setting Up Hugo with Blowfish"
date: 2026-04-17
categories: ["Tutorials"]
tags: ["hugo", "blowfish", "github-pages"]
---

In this post I document how I set up my portfolio using Hugo and the Blowfish theme.

## What I used

- Hugo static site generator
- Blowfish theme
- GitHub Actions for CI/CD
- GitHub Pages for hosting

## Steps

1. Installed Hugo and blowfish-tools via npm
2. Created a new site with `blowfish-tools new portfolio`
3. Connected to GitHub and set up automatic deployment
4. Added a RAG chatbot powered by Dify and OpenAI

## What I learned

Setting up a static site with automatic deployment is surprisingly straightforward
once you understand how GitHub Actions works. Every push to main automatically
rebuilds and redeploys the site.
