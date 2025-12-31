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
| ![GitHub Commit](https://i.imgur.com/placeholder.png) | ![GitLab Mirror](https://i.imgur.com/placeholder.png) |

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
```bash
1. Go to GitLab → Settings → Access Tokens
2. Create token with `api` and `write_repository` scopes
3. Copy the token (it appears only once!)
