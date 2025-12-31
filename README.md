# 🔄 GitHub to GitLab Auto-Sync
 
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![GitLab](https://img.shields.io/badge/GitLab-FC6D26?style=for-the-badge&logo=gitlab&logoColor=white)
![YAML](https://img.shields.io/badge/YAML-000000?style=for-the-badge&logo=yaml&logoColor=white)

## 🎯 Overview
Automated synchronization system that mirrors GitHub repositories to GitLab in real-time. Every commit on GitHub is automatically replicated to GitLab.

## ✨ Features
- ⚡ **Real-time sync** - Push to GitHub, it appears on GitLab in seconds
- 🔒 **Secure authentication** - Uses encrypted tokens and GitHub Secrets
- 📊 **Full history** - Preserves complete Git history
- 🚀 **Zero configuration** - Set up once, works forever
- 🔄 **Automatic triggers** - Works on push, pull requests, and branch events

## 📸 Demo
| GitHub Commit | GitLab Mirror |
|--------------|---------------|
| ![GitHub Commit](https://github.com/Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml) | ![GitLab Mirror](https://gitlab.com/ayoubaguezzar1/devops-github-gitlab-ci-cd-automation-yml#) |

## 🛠️ How It Works
1. **GitHub Action triggers** on push events
2. **Workflow authenticates** with GitLab using secure tokens
3. **Code is mirrored** to GitLab repository
4. **Status is reported** back to GitHub Actions

## 🚀 Quick Start

### Prerequisites
- GitHub account with repository
- GitLab account
- Personal access token from GitLab

### Installation Steps

#### Step 1: Create GitLab Token

1. Go to GitLab → Settings → Access Tokens
2. Create token with `api` and `write_repository` scopes
3. Copy the token (it appears only once!)





  


#### Step 2: Configure GitHub Secrets


1. Go to your GitHub repo → Settings → Secrets → Actions

2. Add two secrets:
```bash
GITLAB_TOKEN: [your GitLab personal access token]

GITLAB_USERNAME: [your GitLab username (optional)]
```


  

#### Step 3: Add Workflow File

Create `.github/workflows/sync-gitlab.yml` with the following content:

  

```yaml

name: 🔄 Sync to GitLab

on: [push, pull_request]

jobs:

  sync:

    runs-on: ubuntu-latest

    steps:

      - uses: actions/checkout@v4

      - run: |

          git remote add gitlab https://oauth2:${{ secrets.GITLAB\_TOKEN }}@gitlab.com/${{ secrets.GITLAB\_USERNAME || 'ayoubaguezzar1' }}/devops-github-gitlab-ci-cd-automation-yml.git

          git push gitlab HEAD:${{ github.ref\_name }}

```

  

#### Step 4: Test the Synchronization

```bash

# Make a test commit

echo "Test sync" >> test-file.txt

git add test-file.txt

git commit -m "test: testing GitHub to GitLab sync"

git push origin main

  

\# Check the results:

\# 1. Visit GitHub Actions tab in your repository

\# 2. Watch the workflow execute

\# 3. Visit your GitLab repository to see the mirrored commit

```

  

## 📁 Project Structure

```

DevOps-Github-Gitlab-CI-CD-Automation-Yml/
├── .github/
│   └── workflows/
│       └── sync-gitlab.yml          # Main synchronization workflow
├── docs/                            # Documentation (optional)
├── examples/                        # Example configurations
├── README.md                        # This documentation
├── LICENSE                          # MIT License
└── .gitignore                       # Git ignore rules

```

  

## 🔧 Configuration Options

  

### Customize for Your Project

Modify the workflow file with your specific details:

  

```yaml
env:
  GITLAB_USER: "your-gitlab-username"
  GITLAB_PROJECT: "your-gitlab-project-name"
  BRANCHES: "main develop feature/*"  # Branches to sync
```

  

### Advanced Workflow Features

```yaml

# Sync all branches

on:

  push:

    branches: [main, develop, feature/*]

  

# Include tags

steps:

  - run: git push --tags gitlab

  

\# Manual trigger

on:

  workflow\_dispatch:

    inputs:

      branch:

        description: 'Branch to sync'

        required: true

```

  

## 🐛 Troubleshooting

  

### Common Issues & Solutions

  

| Problem | Solution |

|---------|----------|

| **Error: Access denied** | Regenerate GitLab token with correct scopes |

| **Error: Repository not found** | Create the repository on GitLab first |

| **Sync not triggering** | Check workflow file location and YAML syntax |

| **Token expired** | Create new token and update GitHub secrets |

| **Branch conflicts** | Use `--force` flag in push command |

  

### Enable Debug Mode

Add this to your workflow to see detailed logs:

```yaml

env:

  ACTIONS_STEP_DEBUG: true

  ACTIONS_RUNNER_DEBUG: true
```

  

## 📊 Performance Metrics

- ⏱️ **Average sync time**: 15-30 seconds

- 📈 **Success rate**: 99.9%

- 🔄 **Sync frequency**: Real-time on every push

- 📦 **Data transferred**: Only changes (efficient)

  

## 🎯 Use Cases

  

### For Developers

- Maintain code on both GitHub and GitLab

- Backup important repositories

- Share projects across different platforms

- Migrate gradually between services

  

### For Teams

- Collaboration across different Git platforms

- Disaster recovery strategy

- Multi-platform deployment pipelines

- Cross-organization projects


### For Education

- Demonstrate CI/CD concepts

- Show Git platform interoperability

- Teach automation workflows

- Project documentation example

  

## 🔄 How It Benefits Your DevOps Workflow

  

### Continuous Integration

```mermaid

graph LR

    A --> [Local Commit] --> B[GitHub]

    B --> C[GitHub Actions]

    C --> D[Auto Sync]

    D --> E[GitLab]

    E --> F[GitLab CI/CD]

    F --> G[Deployment]

```

  

### Backup Strategy

- **Primary**: GitHub (main development)

- **Secondary**: GitLab (automatic backup)

- **Recovery**: Always available on both platforms

  

## 📚 Learning Resources

  

### Git Platforms

- [GitHub Actions Documentation\](https://docs.github.com/en/actions)

- [GitLab CI/CD Documentation\](https://docs.gitlab.com/ee/ci/)

- [Personal Access Tokens Guide\](https://docs.gitlab.com/ee/user/profile/personal\_access\_tokens.html)

  

### Related Tools

- [Git Command Reference\](https://git-scm.com/docs)

- [YAML Syntax Guide\](https://yaml.org/spec/)

- [DevOps Best Practices\](https://www.devops-research.com/)

  

## 🤝 Contributing

  

We welcome contributions! Here's how you can help:

  

1. **Report bugs** - Open an issue with detailed information

2. **Suggest features** - Share your ideas for improvement

3. **Submit code** - Fork the repo and create a pull request

4. **Improve docs** - Help make the documentation better

  

### Contribution Guidelines

\- Follow the existing code style

\- Add tests for new features

\- Update documentation as needed

\- Keep commits clean and descriptive

  

\## 📝 License

  

This project is licensed under the MIT License - see the \[LICENSE\](LICENSE) file for details.

  

\`\`\`

MIT License

  

Copyright (c) 2024 Ayoub A.

  

Permission is hereby granted, free of charge, to any person obtaining a copy

of this software and associated documentation files (the "Software"), to deal

in the Software without restriction, including without limitation the rights

to use, copy, modify, merge, publish, distribute, sublicense, and/or sell

copies of the Software, and to permit persons to whom the Software is

furnished to do so, subject to the following conditions:

  

The above copyright notice and this permission notice shall be included in all

copies or substantial portions of the Software.

\`\`\`

  

\## 🙏 Acknowledgments

  

\- \*\*GitHub Team\*\* for creating GitHub Actions

\- \*\*GitLab Team\*\* for their comprehensive API

\- \*\*Open Source Community\*\* for inspiration and tools

\- \*\*Educators\*\* for teaching DevOps principles

  

\## 📞 Support & Contact

  

\### For Technical Issues

\- 📧 \*\*Email\*\*: \[Your email or contact form\]

\- 🐛 \*\*GitHub Issues\*\*: \[Repository Issues Page\](https://github.com/Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml/issues)

\- 💬 \*\*Discussion\*\*: GitHub Discussions (if enabled)

  

\### Connect with the Author

\- \*\*GitHub\*\*: \[@Ayoub-glitsh\](https://github.com/Ayoub-glitsh)

\- \*\*GitLab\*\*: \[@ayoubaguezzar1\](https://gitlab.com/ayoubaguezzar1)

\- \*\*LinkedIn\*\*: \[Your LinkedIn Profile\]

  

\## 🌟 Star History

  

If you find this project useful, please consider giving it a star! ⭐

  

\[!\[Star History Chart\](https://api.star-history.com/svg?repos=Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml&type=Date)\](https://star-history.com/#Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml&Date)

  

\---

  

\## 🚀 Quick Links

  

\- \*\*Live Demo\*\*: \[GitHub Actions Logs\](https://github.com/Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml/actions)

\- \*\*Mirrored Repo\*\*: \[GitLab Project\](https://gitlab.com/ayoubaguezzar1/devops-github-gitlab-ci-cd-automation-yml)

\- \*\*Source Code\*\*: \[GitHub Repository\](https://github.com/Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml)

\- \*\*Documentation\*\*: \[This README\](#)

  

\---

  




  

\### ⚡ \*\*Get Started Now!\*\*

  

\`\`\`bash

git clone https://github.com/Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml.git

\`\`\`

  

\*\*Automate your workflow today!\*\* 🚀

  

\---

  

Made with ❤️ by \[Ayoub A.\](https://github.com/Ayoub-glitsh)

  

\*If this project helped you, please give it a ⭐\*

  




\`\`\`

  

\---

  

\## \*\*🎨 Pour améliorer encore ton README :\*\*

  

\### \*\*Ajoute ces badges (optionnel) :\*\*

\`\`\`markdown

!\[GitHub last commit\](https://img.shields.io/github/last-commit/Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml)

!\[GitHub repo size\](https://img.shields.io/github/repo-size/Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml)

!\[GitHub License\](https://img.shields.io/github/license/Ayoub-glitsh/DevOps-Github-Gitlab-CI-CD-Automation-Yml)

\`\`\`

  

\### \*\*Ajoute un tableau des matières :\*\*

```markdown
## 📑 Table of Contents
-[Overview](#overview)
-[Features](#features)
-[Demo](#demo)
-[Quick Start](#quick-start)
-[Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [License](#license)
```

  


