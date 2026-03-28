# Lead Sniper — n8n Workflow

Automated High-Value Lead tracker that monitors GitHub repository stars.

## Tools Used

- n8n (workflow automation)
- GitHub API (stargazers + user enrichment)
- Google Gemini (sales pitch generation)
- Slack (webhook notifications)

## Workflow

1. Schedule Trigger (every 15 min)
2. Fetch stargazers from GitHub repo
3. Enrich each user profile
4. Filter: followers > 100 OR public_repos > 50
5. Generate AI sales pitch
6. Post formatted alert to Slack

## Screenshots

### n8n Workflow
![n8n Workflow](n8n_workflow.png)

### Slack Output
![Slack Output](slack_output.png)

## Setup

### Prerequisites

- [n8n](https://n8n.io/) instance (self-hosted or cloud)
- GitHub Personal Access Token (PAT) with public repo read scope
- Google Gemini API key
- Slack Incoming Webhook URL

### Steps

1. **Import the workflow**
   - In n8n, go to **Workflows → Import**
   - Upload `Lead_Sniper_Workflow.json`

2. **Set up credentials**
   - **GitHub PAT**: In n8n, create a new *Header Auth* credential named `Lead Sniper`
     - Header Name: `Authorization`
     - Header Value: `Bearer <your_github_token>`
   - **Google Gemini**: Create a new *Google Gemini(PaLM) Api* credential named `Lead Sniper`
     - Paste your Gemini API key

3. **Configure the Slack webhook**
   - In the `Post to Slack` node, replace the URL with your Slack Incoming Webhook URL

4. **Set the target repo**
   - In the `Get Stargazers` node, update the URL to point to your GitHub repo:
     ```
     https://api.github.com/repos/{owner}/{repo}/stargazers
     ```

5. **Activate the workflow**
   - Toggle the workflow to **Active** — it will run every 15 minutes automatically
