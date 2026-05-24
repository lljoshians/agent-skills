# Agent Skills

A fork of [WordPress/agent-skills](https://github.com/WordPress/agent-skills) — a collection of reusable AI agent skills for automating common WordPress development workflows.

## Overview

This repository contains a curated set of skills that can be used by AI agents to assist with:

- **Code Review** — Automated PR analysis, style checks, and feedback
- **Issue Triage** — Labeling, prioritizing, and routing issues
- **Upstream Sync** — Keeping forks in sync with upstream repositories
- **Props Management** — Tracking and attributing contributors
- **CI Maintenance** — Monitoring and responding to workflow failures

## Skills

| Skill | Description | Workflow |
|-------|-------------|----------|
| `ai-skill-maintenance` | Monitors and maintains AI skill definitions | `.github/workflows/ai-skill-maintenance.yml` |
| `upstream-sync` | Syncs fork with upstream changes | `.github/workflows/upstream-sync.yml` |
| `props-bot` | Manages contributor props on PRs/commits | `.github/workflows/props-bot.yml` |
| `ci` | Runs continuous integration checks | `.github/workflows/ci.yml` |

## Getting Started

### Prerequisites

- Node.js 18+
- A GitHub repository with Actions enabled
- A GitHub token with appropriate permissions

### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/your-org/agent-skills.git
   cd agent-skills
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Configure your environment:
   ```bash
   cp .env.example .env
   # Edit .env with your settings
   ```

### Usage

Skills are triggered via GitHub Actions workflows. Each workflow can also be run locally using [act](https://github.com/nektos/act):

```bash
act push -W .github/workflows/ci.yml
```

## Configuration

Skill behavior can be customized via repository variables and secrets. See each workflow file for available configuration options.

### Required Secrets

| Secret | Description |
|--------|-------------|
| `GITHUB_TOKEN` | Standard GitHub token (auto-provided) |
| `AI_API_KEY` | API key for AI provider (if using AI features) |

### Repository Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `UPSTREAM_REPO` | `WordPress/agent-skills` | The upstream repository to sync from |
| `SYNC_BRANCH` | `trunk` | Branch to sync from upstream |

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on contributing to this project.

## Fork Differences

This fork includes the following changes from upstream:

- Enhanced CI pipeline with additional linting steps
- Extended props-bot with Slack notification support
- Custom upstream sync conflict resolution strategy

## License

This project is licensed under the terms described in [LICENSE](LICENSE).
