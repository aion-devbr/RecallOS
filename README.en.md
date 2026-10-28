<div align="center">
  <img src="recallos-logo.svg" alt="RecallOS logo" width="100%" />
  <h1>RecallOS</h1>
  <p><strong>Persistent memory for AI agents</strong></p>
  <p>A memory layer designed to help AI agents and applications preserve context across conversations, tools, and sessions.</p>
</div>

<p align="center">
  <a href="README.md">Português (Brasil)</a> &nbsp;&bull;&nbsp;
  <a href="README.en.md">English</a> &nbsp;&bull;&nbsp;
  <a href="README.zh-CN.md">简体中文</a> &nbsp;&bull;&nbsp;
  <a href="README.ja.md">日本語</a> &nbsp;&bull;&nbsp;
  <a href="README.hi.md">हिन्दी</a>
</p>

> **Project revival:** RecallOS is being resumed publicly from the open-source XMem codebase originally published by XortexAI. Features, installation steps, integrations, and benchmark results inherited from that codebase are being reviewed and have not all been revalidated for RecallOS. Original copyright notices and license files remain in the repository.

## What is RecallOS?

AI applications often lose context between conversations, tools, or providers. RecallOS aims to provide a persistent memory layer that stores, organizes, and retrieves useful information over time.

The inherited XMem architecture treats memory as an active process: specialized agents classify information, decide what should be saved or updated, and route each type of data to an appropriate storage backend. Retrieval can combine multiple searches and synthesize an answer with source references. These behaviors are documented from the inherited implementation and will be updated as they are reviewed.

## Features in the inherited codebase

- Browser extension integrations for ChatGPT, Claude, Gemini, DeepSeek, and Perplexity.
- Agent plugins for Claude Code, Codex, Cursor, Hermes, OpenClaw, and OpenCode.
- Conversation import from shared links and transcript files.
- Git repository scanning and code-aware retrieval.
- Multiple LLM providers, including Gemini, Claude, OpenAI, OpenRouter, Amazon Bedrock, and Ollama.
- Local options using Ollama, FastEmbed, Chroma, or SQLite.

See the [Portuguese README](README.md) for the longer feature and architecture overview. Availability and compatibility are still being checked during the project revival.

## Quick start

The documented local workflow uses Node.js, Python, Docker, and Ollama. The commands below clone this repository and run its development setup:

```bash
git clone https://github.com/aion-devbr/RecallOS.git
cd RecallOS
npm run dev
```

The setup may install dependencies, build the browser extension, start local services, and download Ollama models. Review [Local.md](Local.md) and the environment template before running it. The command list was statically compared with the project scripts; the full setup has not yet been executed end to end.

## Documentation

- [Local development guide](Local.md)
- [Configuration](docs/configuration.md)
- [Roadmap](ROADMAP.md)
- [Changelog](CHANGELOG.md)
- [Contributing](CONTRIBUTING.md)
- [License](LICENSE)

## Project status

RecallOS is in an early public revival phase. The repository currently contains the inherited XMem implementation and project documentation updates. Compatibility, installation, tests, and release packaging remain part of the ongoing review.

## Attribution

RecallOS is based on the XMem project by XortexAI. See the original copyright notices and the [BSD 3-Clause License](LICENSE) for attribution and license terms.
