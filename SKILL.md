---
name: airdrop-execution
description: "Execute crypto airdrop / whitelist / quest tasks from websites on the user's behalf. Click-only tasks are automated with the user's public identity; tasks needing X/Twitter connect, wallet signature, or CAPTCHA are escalated to the user with exact steps."
version: 1.0.0
author: Community
license: MIT
platforms: [linux, macos, windows]
tags: [general]
---

# Airdrop Execution — Skill

Execute crypto airdrop / whitelist / quest tasks from websites on the user's behalf. Click-only tasks are automated with the user's public identity; tasks needing X/Twitter connect, wallet signature, or CAPTCHA are escalated to the user with exact steps.

## Install

```bash
cp -r <skill-name> ~/.hermes/skills/<skill-path>/
```

Or clone this repository:

```bash
git clone https://github.com/iizcm/airdrop-execution-skill.git ~/.hermes/skills/<skill-path>/
```

## Usage

Invoke your AI agent with a clear instruction matching this skill's purpose. The agent will route tasks to this skill when the instruction matches its description or trigger keywords.

Refer to `README.md` in this repository for:
- Detailed step-by-step installation guide
- Bilingual documentation (English + Indonesian)
- Troubleshooting table
- Security best practices
- Customization tips

## Safety rules

- Never commit private keys, seed phrases, API tokens, or personal data to version control
- Use placeholders (`<YOUR_...>`) in all examples and code snippets
- Validate all outputs before acting on them
- Keep real credentials in your runtime's secure credential store only
