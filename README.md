# Lead Sniper — n8n Workflow

Automated High-Value Lead tracker that monitors GitHub repository stars.

## Tools Used
- n8n (workflow automation)
- GitHub API (stargazers + user enrichment)
- OpenAI gpt-4o-mini (sales pitch generation)
- Slack (webhook notifications)

## Workflow
1. Schedule Trigger (every 15 min)
2. Fetch stargazers from GitHub repo
3. Enrich each user profile
4. Filter: followers > 100 OR public_repos > 50
5. Generate AI sales pitch
6. Post formatted alert to Slack
