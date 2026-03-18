# PublicNews — GitHub Actions Runner

This repository is a **public runner** for private Telegram bot projects.

It contains only GitHub Actions workflow files and bot state (JSON). No bot source code is stored here.

## How it works

Each workflow clones the private bot repository (using a stored secret token), runs the bot script, then commits updated state files back to this repo.

## Workflows

| Workflow | Schedule | Purpose |
|---|---|---|
| `news_bot.yml` | Every 20 min | Post war/conflict news to Telegram channel |
| `war_summary.yml` | 07:00 & 19:00 UTC | Post daily war summary digest |
| `refresh_conflicts_cache.yml` | Manual | Clear conflicts cache in posted.json |
| `delete_all.yml` | Manual | Delete all messages from Telegram channel |

## State files

| File | Purpose |
|---|---|
| `posted.json` | Deduplication state — posted URLs and titles |
| `war_articles.json` | Article buffer for summary generation |

## Secrets required

Configure these in **Settings → Secrets and variables → Actions**:

| Secret | Description |
|---|---|
| `PRIVATE_REPO_TOKEN` | PAT with read access to the private bot repo |
| `BOT_TOKEN` | Telegram bot token |
| `CHANNEL_ID` | Telegram channel numeric ID |
| `NEWSAPI_KEY` | NewsAPI key |
| `GROQ_API_KEY` | Groq API key |
| `CHANNEL_USERNAME` | Telegram channel username |
| `EXPRESS_CHANNEL_ID` | Express channel numeric ID |
| `EXPRESS_CHANNEL_USERNAME` | Express channel username |
