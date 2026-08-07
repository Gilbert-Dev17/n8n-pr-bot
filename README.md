# AI-Powered PR Documentation Bot (n8n + Claude API + GitHub API)

> Built an automated workflow that triggers on GitHub PR events, orchestrates REST API calls and an LLM to generate structured PR documentation, and posts it back via authenticated API — reducing manual PR-writing time to zero.

## Overview
This project is an automated n8n workflow designed to streamline the pull request documentation process. When a developer opens a PR, the workflow automatically intercepts the event, fetches the associated commit diffs using the GitHub REST API, and uses an LLM (Claude/OpenAI) to generate a well-structured PR description based on a standard template. 
The description is then posted back to the PR via an authenticated API call.

## Architecture
1. **Trigger**: A GitHub Webhook listens for `Pull requests` events (specifically the `opened` action).
2. **Fetch Data**: The workflow calls the GitHub REST API (`GET /repos/{owner}/{repo}/pulls/{pull_number}/commits`) to extract the list of commit messages.
3. **LLM Processing**: The commit data is passed to an LLM node with a system prompt enforcing a strict PR template format.
4. **Post Update**: A final GitHub REST API call (`PATCH` or `POST`) updates the PR description with the generated summary.
*(Insert Architecture Diagram or Screenshot of n8n flow here)*

## Project Setup
1. **n8n Environment**: This workflow is designed for a self-hosted n8n instance (e.g., deployed via Docker).
2. **GitHub Webhooks**: Configure a webhook in your repository settings pointing to your n8n Webhook URL, listening for Pull Request events.
3. **Authentication**: A GitHub Personal Access Token (PAT) with `repo` scope is required to authenticate API calls to fetch commits and post the description.
## Demo
*(Insert GIF or Video link of the bot in action here)*

"Testing my n8n webhook PR trigger!

## Future Enhancements
* Implementing full OAuth App flow for wider distribution.
* Adding fallback notifications (e.g., Telegram/Slack) for LLM or API rate-limiting errors.
* Supporting custom PR templates on a per-repository basis.
