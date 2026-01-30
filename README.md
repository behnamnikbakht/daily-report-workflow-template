# 📊 AI-Powered GitHub Daily Report Action

Automatically generate comprehensive daily activity reports for your GitHub organization using AI-powered summaries.

## ✨ Features

- 🤖 **AI-Generated Summaries** - Google Gemini analyzes actual code changes to explain what each developer accomplished
- 📈 **Organization-Wide Coverage** - Collects data from all repositories in your org
- 📧 **Email Notifications** - Automatic delivery to your team every morning
- 📁 **Smart Organization** - Reports stored as `reports/YYYY/MM/DD.md`
- 🏆 **Top Contributors** - Ranks developers by commits and line changes
- 💰 **Cost Effective** - Runs on GitHub Actions + Gemini free tiers
- 🔄 **Fully Automated** - Set it and forget it

## 📸 What It Looks Like

```markdown
# 📊 Daily Activity Report
**Date:** 2026-01-30

## Summary
| Metric | Value |
|--------|-------|
| 💾 Total Commits | 23 |
| ➕ Lines Added | +2,347 |

### 🏆 Top Contributors
1. **Alice Chen** - 12 commits (+2,456/-789)

## 👥 Developer Activity

### 👤 Alice Chen
**🤖 AI Summary:**
> Implemented real-time notification system using WebSockets...

**Work Accomplished:**
- ✏️ `src/notifications/websocket.ts` (+456/-123)
- 🆕 `src/redis-pubsub.ts` (+234/-0)
```

## 🚀 Quick Start

### 1. Customize the Workflow

Open `.github/workflows/daily-report.yml` and replace:
- `YOUR_ORG_NAME` - Your GitHub organization name
- `your-team@example.com` - Your email address(es)

**See [TEMPLATE_SETUP.md](TEMPLATE_SETUP.md) for detailed instructions.**

### 2. Add Secrets

Go to **Settings → Secrets and variables → Actions** and add:

| Secret | Description | Get It From |
|--------|-------------|-------------|
| `ORG_ACCESS_TOKEN` | GitHub PAT with `repo` + `read:org` | [GitHub Settings](https://github.com/settings/tokens) |
| `GEMINI_API_KEY` | Google AI API key | [Google AI Studio](https://aistudio.google.com/) |
| `EMAIL_USERNAME` | Gmail address | Your Gmail |
| `EMAIL_PASSWORD` | Gmail App Password | [Google Account](https://myaccount.google.com/apppasswords) |

### 3. Run It

- **Manual:** Actions → Daily Report → Run workflow
- **Automatic:** Runs daily at 6:50 AM EST

## 📋 Requirements

- GitHub organization with multiple repositories
- GitHub Actions enabled
- Google AI Studio account (free tier available)
- Gmail account for notifications

## 🎯 What Gets Collected

- ✅ All commits from yesterday
- ✅ All pull requests updated yesterday
- ✅ Actual code diffs and patches
- ✅ Line additions/deletions
- ✅ File changes with status (added/modified/deleted)
- ✅ Commit messages and PR details

## 🤖 AI Analysis

The workflow uses Google Gemini 2.5 Flash to:

1. Read actual code changes (diffs/patches)
2. Analyze commit patterns
3. Understand what was built/fixed
4. Generate 2-3 sentence summaries per developer

**Example AI Output:**
> "Implemented user authentication system with JWT token validation and session management. Added bcrypt password hashing for security and created login/logout API endpoints. Fixed a critical security vulnerability in the token refresh logic."

## 📁 Report Structure

```
reports/
├── 2026/
│   ├── 01/
│   │   ├── 29.md
│   │   ├── 30.md
│   │   └── 31.md
│   └── 02/
│       └── 01.md
```

## ⚙️ Customization

### Change Schedule

Edit the cron expression (default: 6:50 AM EST):

```yaml
on:
  schedule:
    - cron: "50 11 * * *"  # UTC time
```

### Change Email Recipients

```yaml
to: alice@example.com,bob@example.com,team@example.com
```

### Disable Features

- **AI Summaries:** Remove `GEMINI_API_KEY` secret
- **Email:** Remove or comment out the email step
- **Artifacts:** Adjust retention days

## 🔧 Troubleshooting

| Issue | Solution |
|-------|----------|
| "Organization not found" | Check `YOUR_ORG_NAME` is correct |
| "Permission denied" | Verify `ORG_ACCESS_TOKEN` has `repo` + `read:org` scopes |
| "Email failed" | Check Gmail App Password (not regular password) |
| "No AI summaries" | Verify `GEMINI_API_KEY` is valid |

**See [TEMPLATE_SETUP.md](TEMPLATE_SETUP.md) for detailed troubleshooting.**

## 💡 Use Cases

- **Team Standups** - Skip the meeting, read the report
- **Manager Updates** - See organization activity at a glance
- **Performance Reviews** - Historical data on contributions
- **Project Tracking** - Monitor progress across repos
- **Knowledge Sharing** - Learn what others are working on

## 📊 Cost

- **GitHub Actions:** 2,000 minutes/month free
- **Google Gemini:** Free tier with generous limits
- **Total:** ~$0/month for most teams 🎉

## 🤝 Contributing

Contributions welcome! Feel free to:

- 🐛 Report bugs via Issues
- 💡 Suggest features
- 🔧 Submit pull requests
- ⭐ Star the repository

## 📄 License

MIT License - feel free to use and modify for your organization.

## 🔗 Links

- [Setup Guide](TEMPLATE_SETUP.md) - Detailed customization instructions
- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [Google Gemini API](https://ai.google.dev/docs)

## 💬 Support

- 📝 Open an issue for bugs or questions
- ⭐ Star the repo if you find it useful
- 🔄 Share with your team

---

**Built with ❤️ using GitHub Actions + Google Gemini**

*Automate your team's daily reporting in minutes!*
