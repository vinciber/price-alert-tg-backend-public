# Price Alert TG Backend - Public Workflows

This repository hosts the GitHub Actions workflows for the [Private Price Alert Backend](https://github.com/vinciber/price-alert-tg-backend).

## 🚀 Purpose
To utilize GitHub's free tier for public repositories for running scheduled maintenance and scraper tasks, while keeping the core business logic and sensitive code in a private repository.

> [!NOTE]
> **Pure Workflow Runner**: This repository does NOT host any static assets (like HTML or CSS). All legal pages (`privacy.html`, `tos.html`) and donation pages (`donate.html`) are hosted via the private repository's Vercel deployment. 

## 🔒 Security
- **No Source Code**: This repository does not contain the actual application code.
- **Secrets Management**: All sensitive credentials (API keys, Tokens, URLs) are stored in GitHub Secrets.
- **Private Access**: The workflows use a `PRIVATE_REPO_PAT` to check out the private repository securely at runtime.

## 🛠 Workflows
| Workflow | Description | Schedule | Source Code Origin |
|----------|-------------|----------|--------------------|
| `daily_etf_scrape.yml` | Updates ETF data daily | 06:00 & 22:00 UTC | Private Repo |
| `fast-checks.yml` | Frequent crypto checks | Every 10m | Private Repo |
| `mega_signal.yml` | Trend analysis | Hourly | Private Repo |
| `news_update.yml` | News scraper | Every 30m | Private Repo |
| `slow-checks.yml` | Deep technical analysis | 3,18,33,48rd min | Private Repo |
| `whale_scraper.yml` | Whale alert scraper | Every 6h | Private Repo |
| `check_mobile_alerts.yml` | Mobile alert checks | Every 15m | Private Repo |

## ⚙️ Setup for Maintainers

1. **Secrets Required**:
   - `PRIVATE_REPO_PAT`: A Personal Access Token with `repo` scope to checkout the private backend code.
   - All other app secrets (`APP_SECRET_KEY`, `TELEGRAM_BOT_TOKEN`, etc.)

2. **Modifying Workflows**:
   - Updates should be pushed here.
   - Ensure `checkout` step always references the private repo.

## License
MIT
