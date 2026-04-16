<div align="center">

[![Repo Gardener Banner](https://raw.githubusercontent.com/Shineii86/RepoGardener/main/images/RepoGardener.png)](https://github.com/Shineii86/RepoGardener)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Shineii86/RepoGardener/blob/main/notebooks/RepoGardener.ipynb)
[![Python 3.8+](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[![GitHub Stars](https://img.shields.io/github/stars/Shineii86/RepoGardener?style=for-the-badge)](https://github.com/Shineii86/RepoGardener/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/Shineii86/RepoGardener?style=for-the-badge)](https://github.com/Shineii86/RepoGardener/fork)

**Automatically scan, audit, and update dependencies across Python, Node.js, Java, and Go projects — right from Google Colab.**

</div>

---

> ℹ️ **ABOUT THIS TOOL**
> - This script scans all your GitHub repositories for outdated dependencies across multiple package managers and can optionally open pull requests to update them.
> - **Supported ecosystems**: Python (`requirements.txt`), Node.js (`package.json`), Java (`pom.xml`), Go (`go.mod`).
> - You need a **Personal Access Token (classic)** with `repo` and `workflow` scopes.
> - This is a powerful automation tool. Use it responsibly and review changes before merging.

---

## 🎯 What is This Tool?

**Repo Gardener** is a multi‑ecosystem dependency management assistant for your GitHub repositories. It helps you:

- **Discover** outdated dependencies across all your projects.
- **Audit** exactly which packages need updates.
- **Automate** the creation of pull requests to apply those updates.

Think of it as your own personal, customizable Dependabot that works across Python, Node.js, Java, and Go — all at once.

---

## ✨ Features

| Feature                      | Description                                                                 |
|------------------------------|-----------------------------------------------------------------------------|
| 🔍 **Multi‑Repo Scanning**    | Scan all your repositories or a filtered subset.                            |
| 🐍 **Python**                | Parses `requirements.txt` and checks PyPI.                                  |
| 🟢 **Node.js**               | Parses `package.json` (dependencies + devDependencies) and checks npm.      |
| ☕ **Java**                  | Parses `pom.xml` and checks Maven Central.                                  |
| 🐹 **Go**                    | Parses `go.mod` and checks the Go module proxy.                             |
| 📊 **Detailed Reporting**    | Shows exactly which packages are outdated in which repositories.            |
| 🔀 **Automated PR Creation**  | Creates a single PR per repository with all ecosystem updates.              |
| ⏰ **Schedulable**            | Run it weekly from Colab to keep dependencies perpetually fresh.            |
| 🧩 **Easily Extensible**      | Add support for more package managers via a simple class interface.         |

---

## 🛠️ Prerequisites

1. **A GitHub account**.
2. **A Personal Access Token (classic)** with `repo` and `workflow` scopes.

### 🔑 How to Get a Personal Access Token

1. Go to **Settings** → **Developer settings** → **Personal access tokens** → **Tokens (classic)**.
2. Click **Generate new token (classic)**.
3. Check the **`repo`** and **`workflow`** scopes.
4. Generate and copy the token.

---

## 🚀 Quick Start

1. **Click the "Open in Colab" badge** above.
2. **Fill in your GitHub username and token**.
3. **Select ecosystems** to scan (e.g., `python,node,java,go`).
4. **Choose your mode**: `scan` (report only) or `update` (scan + create PRs).
5. **(Optional)** Filter to specific repositories.
6. **Run all cells** (Ctrl+F9).

You'll see a detailed report of any outdated dependencies across your projects.

---

## ⚙️ Configuration Options

| Parameter      | Description                                                               |
|----------------|---------------------------------------------------------------------------|
| `USERNAME`     | Your GitHub username.                                                      |
| `TOKEN`        | Personal Access Token with `repo` and `workflow` scopes.                   |
| `MODE`         | `scan` to only report, `update` to also create PRs.                        |
| `REPO_FILTER`  | Comma‑separated list of repo names to scan (leave blank for all).          |
| `ECOSYSTEMS`   | Comma‑separated list: `python`, `node`, `java`, `go`.                      |
| `ACTION_DELAY` | Seconds to wait between API calls (avoid rate limits).                     |

---

## 🔬 How It Works

1. **GitHub API**: Fetches all repositories for the authenticated user.
2. **File Detection**: For each repo, looks for known dependency files.
3. **Parsing**: Extracts package names and current versions using ecosystem‑specific parsers.
4. **Version Checking**: Queries the relevant registry (PyPI, npm, Maven Central, Go proxy) for the latest version.
5. **Comparison**: Uses semantic versioning to identify outdated packages.
6. **Branch & PR**: In `update` mode, creates a branch, updates all outdated files, and opens a single pull request per repository.

---

## 🧩 Extending to Other Package Managers

The script is built around an abstract `PackageManager` class. To add support for a new ecosystem:

```python
class MyNewManager(PackageManager):
    def name(self):
        return "My Ecosystem"

    def filename(self):
        return "my_deps.file"

    def parse_dependencies(self, content):
        # Return dict of package -> version
        pass

    def get_latest_version(self, package_name):
        # Query the registry
        pass

    def update_file(self, content, outdated):
        # Return updated file content
        pass
```

Then add an instance to `get_managers()`.

---

## 📅 Scheduling

To run this weekly:
1. In Colab, go to **Tools → Command Palette** (Ctrl+Shift+P).
2. Search for **"Run on schedule"**.
3. Set a schedule (e.g., every Monday at 9 AM).
4. Save the notebook to your Google Drive.

---

## 📄 License & Disclaimer

This project is licensed under the **MIT License**.

> ℹ️ This tool is intended to assist developers in maintaining healthy codebases. Always review automated pull requests before merging.

---

### 🔗 Quick Links

- [Google Colab](https://colab.research.google.com/)
- [GitHub Personal Access Tokens](https://github.com/settings/tokens)
- [PyPI JSON API](https://warehouse.pypa.io/api-reference/json.html)
- [npm Registry](https://registry.npmjs.org/)
- [Maven Central Search](https://search.maven.org/)
- [Go Module Proxy](https://proxy.golang.org/)

---

## 💕 Loved My Work?

🚨 [Follow me on GitHub](https://github.com/Shineii86)

⭐ [Give a star to this project](https://github.com/Shineii86/RepoGardener)

<div align="center">

<a href="https://github.com/Shineii86/RepoGardener">
<img src="https://github.com/Shineii86/AniPay/blob/main/Source/Banner6.png" alt="Banner">
</a>
  
  *For inquiries or collaborations*
     
[![Telegram Badge](https://img.shields.io/badge/-Telegram-2CA5E0?style=flat&logo=Telegram&logoColor=white)](https://telegram.me/Shineii86 "Contact on Telegram")
[![Instagram Badge](https://img.shields.io/badge/-Instagram-C13584?style=flat&logo=Instagram&logoColor=white)](https://instagram.com/ikx7.a "Follow on Instagram")
[![Pinterest Badge](https://img.shields.io/badge/-Pinterest-E60023?style=flat&logo=Pinterest&logoColor=white)](https://pinterest.com/ikx7a "Follow on Pinterest")
[![Gmail Badge](https://img.shields.io/badge/-Gmail-D14836?style=flat&logo=Gmail&logoColor=white)](mailto:ikx7a@hotmail.com "Send an Email")

  <sup><b>Copyright © 2026 <a href="https://telegram.me/Shineii86">Shinei Nouzen</a> All Rights Reserved</b></sup>

![Last Commit](https://img.shields.io/github/last-commit/Shineii86/RepoGardener?style=for-the-badge)

</div>
