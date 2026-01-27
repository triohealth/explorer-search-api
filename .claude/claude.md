# Explorer Search API - Claude Code Guide

This repo is commonly used with Claude Code to search clinical notes. Here are quick tips to get started.

## Setup

1. **API Key**: Set up your API key in the system-wide config (recommended):
   ```bash
   mkdir -p ~/.trioexplorer
   echo "TRIOEXPLORER_API_KEY=ts_your_api_key_here" > ~/.trioexplorer/.env
   ```

   The CLI checks for the API key in this order:
   1. `~/.trioexplorer/.env` (system-wide, recommended)
   2. `.env` in the current directory or repo root
   3. `TRIOEXPLORER_API_KEY` environment variable

2. **Install the CLI** (for quick testing):
   ```bash
   pip install -e cli/
   ```

## Quick Testing with trioexplorer CLI

The `trioexplorer` CLI is the fastest way to test searches:

```bash
# Basic search (API key auto-loaded from ~/.trioexplorer/.env)
trioexplorer search "diabetes management"

# Limit results
trioexplorer search "chest pain" -k 5

# Semantic search
trioexplorer search "patient struggling with blood sugar" -t semantic

# List available cohorts
trioexplorer list cohorts
```

## Common Search Parameters

- `query`: Your search text (required)
- `-k`: Number of results (default: 10)
- `-t` / `--search-type`: `hybrid`, `semantic`, or `keyword`
- `--cohort-ids`: Filter by cohort IDs (comma-separated)
