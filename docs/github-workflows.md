# GitHub Workflows for Documentation

## Overview

This guide covers how to use Git and GitHub effectively for version control and collaboration on documentation projects. Learn the workflows that professional teams use to create, review, and publish high-quality documentation.

## Table of Contents

- [Git Fundamentals](#git-fundamentals)
- [GitHub Basics](#github-basics)
- [Repository Setup](#repository-setup)
- [Daily Workflow](#daily-workflow)
- [Branching Strategies](#branching-strategies)
- [Collaboration Workflows](#collaboration-workflows)
- [Pull Request Process](#pull-request-process)
- [GitHub Features for Documentation](#github-features-for-documentation)
- [Advanced Workflows](#advanced-workflows)
- [Best Practices](#best-practices)

---

## Git Fundamentals

### What is Git?

Git is a distributed version control system that tracks changes to files over time. For documentation:
- **Version History**: See every change ever made
- **Collaboration**: Multiple people can work simultaneously
- **Backup**: Your work is safely stored
- **Experimentation**: Try changes without breaking the main version

### Installing Git

**Windows**:
```bash
# Download from git-scm.com
# Or use package manager
winget install Git.Git
```

**macOS**:
```bash
# Install via Homebrew
brew install git

# Or download from git-scm.com
```

**Linux**:
```bash
# Debian/Ubuntu
sudo apt-get install git

# Fedora
sudo dnf install git

# Arch
sudo pacman -S git
```

### Initial Git Configuration

```bash
# Set your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default branch name
git config --global init.defaultBranch main

# Set default editor (VS Code)
git config --global core.editor "code --wait"

# Enable color output
git config --global color.ui auto

# Set line ending handling
# Windows:
git config --global core.autocrlf true
# Mac/Linux:
git config --global core.autocrlf input
```

### Essential Git Commands

| Command | Purpose |
|---------|---------|
| `git init` | Initialize a new Git repository |
| `git clone <url>` | Copy a repository from GitHub |
| `git status` | Check current state of repository |
| `git add <file>` | Stage files for commit |
| `git commit -m "message"` | Save changes with a message |
| `git push` | Upload commits to GitHub |
| `git pull` | Download changes from GitHub |
| `git branch` | List, create, or delete branches |
| `git checkout <branch>` | Switch to a different branch |
| `git merge <branch>` | Merge another branch into current |

---

## GitHub Basics

### What is GitHub?

GitHub is a cloud-based hosting service for Git repositories with additional collaboration features:
- **Remote Storage**: Backup and access from anywhere
- **Collaboration**: Issues, Pull Requests, Discussions
- **Project Management**: Projects, Milestones, Labels
- **Publishing**: GitHub Pages for documentation sites
- **Automation**: GitHub Actions for CI/CD

### Creating a GitHub Account

1. Go to [github.com](https://github.com)
2. Click "Sign up"
3. Follow the registration process
4. Verify your email address
5. Complete your profile

### SSH Key Setup (Recommended)

**Why SSH?**: More secure, no password prompts

**Generate SSH Key**:
```bash
# Generate new SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Start SSH agent
eval "$(ssh-agent -s)"

# Add key to agent
ssh-add ~/.ssh/id_ed25519
```

**Add to GitHub**:
1. Copy public key: `cat ~/.ssh/id_ed25519.pub`
2. GitHub → Settings → SSH and GPG keys → New SSH key
3. Paste key and save
4. Test: `ssh -T git@github.com`

### Personal Access Tokens (Alternative to SSH)

**When to use**: HTTPS instead of SSH

**Create Token**:
1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Generate new token
3. Select scopes (minimum: `repo`)
4. Copy token (save securely!)

**Use Token**:
```bash
# When prompted for password, use token instead
git clone https://github.com/username/repo.git
Username: your-username
Password: <paste-token-here>
```

---

## Repository Setup

### Creating a New Repository on GitHub

**Option 1: GitHub Website**

1. Click "+" in top-right → "New repository"
2. Fill in details:
   - Repository name: `my-documentation`
   - Description: "Project documentation"
   - Public or Private
   - ✅ Add README
   - ✅ Add .gitignore (choose template if applicable)
   - ✅ Choose license (MIT, Apache, etc.)
3. Click "Create repository"

**Option 2: GitHub CLI**

```bash
# Install GitHub CLI (gh)
# See: https://cli.github.com/

# Create repository
gh repo create my-documentation --public --description "Project documentation"

# Or with interactive prompts
gh repo create
```

### Cloning a Repository

```bash
# Clone via SSH (recommended)
git clone git@github.com:username/repository.git

# Clone via HTTPS
git clone https://github.com/username/repository.git

# Clone to specific folder
git clone git@github.com:username/repository.git my-folder

# Navigate to repository
cd repository
```

### Initializing an Existing Project

```bash
# Navigate to your documentation folder
cd my-documentation

# Initialize Git repository
git init

# Add files
git add .

# First commit
git commit -m "Initial commit: Add project documentation"

# Connect to GitHub
git remote add origin git@github.com:username/my-documentation.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Repository Structure for Documentation

```
my-documentation/
├── .git/                 # Git metadata (don't edit)
├── .gitignore           # Files to ignore
├── README.md            # Repository overview
├── LICENSE              # License file
├── docs/                # Documentation files
│   ├── getting-started.md
│   ├── api-reference.md
│   └── guides/
├── images/              # Images and diagrams
└── .github/             # GitHub-specific files
    ├── ISSUE_TEMPLATE/
    ├── PULL_REQUEST_TEMPLATE.md
    └── workflows/       # GitHub Actions
```

### Creating .gitignore

```bash
# .gitignore - Specify files Git should ignore

# OS files
.DS_Store
Thumbs.db

# Editor files
.vscode/
.idea/
*.swp
*.swo

# Build outputs
_site/
dist/
build/

# Temporary files
*.tmp
*.bak
~$*

# Environment files
.env
.env.local

# Node modules (if using static site generator)
node_modules/

# Logs
*.log
```

---

## Daily Workflow

### Basic Documentation Workflow

```bash
# 1. Start your day - Get latest changes
git pull origin main

# 2. Check status
git status

# 3. Make your changes
# Edit documentation files in VS Code

# 4. Review changes
git status
git diff

# 5. Stage changes
git add docs/new-guide.md
# Or stage all changes:
git add .

# 6. Commit with descriptive message
git commit -m "docs: add installation guide for Windows users"

# 7. Push to GitHub
git push origin main
```

### Viewing Changes

```bash
# See what files changed
git status

# See line-by-line changes (unstaged)
git diff

# See changes in staged files
git diff --staged

# See changes in specific file
git diff docs/README.md

# View commit history
git log

# Pretty log with graph
git log --oneline --graph --all

# View specific commit
git show <commit-hash>
```

### Undoing Changes

```bash
# Discard changes in working directory (unstaged)
git checkout -- docs/file.md

# Unstage a file (keep changes)
git reset HEAD docs/file.md

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes) ⚠️ DESTRUCTIVE
git reset --hard HEAD~1

# Revert a commit (creates new commit)
git revert <commit-hash>
```

---

## Branching Strategies

### Why Use Branches?

Branches let you:
- Work on features without affecting the main documentation
- Experiment safely
- Review changes before merging
- Collaborate without conflicts

### Basic Branch Operations

```bash
# List branches
git branch

# Create new branch
git branch feature/add-api-docs

# Switch to branch
git checkout feature/add-api-docs

# Create and switch in one command
git checkout -b feature/add-api-docs

# Push branch to GitHub
git push -u origin feature/add-api-docs

# Delete local branch
git branch -d feature/add-api-docs

# Delete remote branch
git push origin --delete feature/add-api-docs
```

### Branch Naming Conventions

```bash
# Feature branches
feature/add-installation-guide
feature/update-api-reference

# Documentation updates
docs/improve-readme
docs/add-examples

# Bug fixes
fix/broken-links
fix/typos-in-guide

# Experimental
experimental/new-structure
```

### Branching Workflow Example

```bash
# 1. Start with main branch
git checkout main
git pull origin main

# 2. Create feature branch
git checkout -b docs/add-deployment-guide

# 3. Make changes and commit
# ... edit files ...
git add docs/deployment-guide.md
git commit -m "docs: add deployment guide for cloud platforms"

# 4. Push branch to GitHub
git push -u origin docs/add-deployment-guide

# 5. Create Pull Request on GitHub (see next section)

# 6. After PR is merged, cleanup
git checkout main
git pull origin main
git branch -d docs/add-deployment-guide
```

---

## Collaboration Workflows

### Fork and Pull Request Workflow

**Best for**: Open source projects, external contributors

**Workflow**:

1. **Fork the Repository**
   - Go to repository on GitHub
   - Click "Fork" button
   - Creates your own copy

2. **Clone Your Fork**
   ```bash
   git clone git@github.com:your-username/original-repo.git
   cd original-repo
   ```

3. **Add Upstream Remote**
   ```bash
   git remote add upstream git@github.com:original-owner/original-repo.git
   ```

4. **Create Branch**
   ```bash
   git checkout -b docs/my-contribution
   ```

5. **Make Changes and Push**
   ```bash
   # Make changes
   git add .
   git commit -m "docs: improve installation instructions"
   git push origin docs/my-contribution
   ```

6. **Create Pull Request**
   - Go to your fork on GitHub
   - Click "Compare & pull request"
   - Fill in description
   - Submit

7. **Keep Fork Updated**
   ```bash
   git checkout main
   git pull upstream main
   git push origin main
   ```

### Shared Repository Workflow

**Best for**: Team projects, internal documentation

**Workflow**:

1. **Clone Repository**
   ```bash
   git clone git@github.com:organization/docs.git
   ```

2. **Create Feature Branch**
   ```bash
   git checkout -b docs/update-api-reference
   ```

3. **Make Changes**
   ```bash
   # Edit files
   git add docs/api-reference.md
   git commit -m "docs: update API endpoints for v2.0"
   ```

4. **Push and Create PR**
   ```bash
   git push -u origin docs/update-api-reference
   # Create PR on GitHub
   ```

5. **Review and Merge**
   - Team reviews PR
   - Address feedback
   - Merge when approved

### Handling Merge Conflicts

**What is a merge conflict?**
When two people edit the same lines in a file.

**Resolving Conflicts**:

```bash
# 1. Pull latest changes
git pull origin main

# 2. If conflict occurs, Git will notify you
# CONFLICT (content): Merge conflict in docs/README.md

# 3. Open conflicted file in VS Code
# You'll see conflict markers:
<<<<<<< HEAD
Your changes
=======
Their changes
>>>>>>> branch-name

# 4. Edit file to resolve conflict
# Remove conflict markers and choose final version

# 5. Stage resolved file
git add docs/README.md

# 6. Complete merge
git commit -m "docs: resolve merge conflict in README"

# 7. Push
git push origin main
```

**VS Code Conflict Resolution**:
- VS Code highlights conflicts
- Click "Accept Current Change", "Accept Incoming Change", or "Accept Both Changes"
- Save and commit

---

## Pull Request Process

### Creating a Pull Request

**Step 1: Push Your Branch**
```bash
git push -u origin feature/add-troubleshooting-guide
```

**Step 2: On GitHub**

1. Go to repository on GitHub
2. Click "Pull requests" tab
3. Click "New pull request"
4. Select your branch
5. Click "Create pull request"

**Step 3: Fill PR Template**

```markdown
## Description
Add comprehensive troubleshooting guide for common issues

## Type of Change
- [ ] Bug fix (documentation error)
- [x] New content (new documentation)
- [ ] Update (improving existing docs)
- [ ] Breaking change (reorganization)

## Changes Made
- Added troubleshooting-guide.md with common issues
- Updated README.md to link to new guide
- Added screenshots for clarity

## Checklist
- [x] Spell-checked content
- [x] Tested all links
- [x] Added to table of contents
- [x] Follows style guide

## Related Issues
Closes #42
```

### Pull Request Best Practices

**Good PR Title Examples**:
```
docs: add troubleshooting guide for installation issues
fix: correct broken links in API reference
update: improve code examples in getting started guide
```

**PR Description Should Include**:
- What changed and why
- How to test/verify
- Screenshots (if applicable)
- Related issues

**Keep PRs Focused**:
- ✅ One topic per PR
- ✅ Related changes together
- ❌ Mixing unrelated updates

### Reviewing Pull Requests

**As a Reviewer**:

1. **Read the Description**
   - Understand what's being changed

2. **Review Files Changed**
   - Click "Files changed" tab
   - Review line-by-line

3. **Leave Comments**
   - Click line numbers to comment
   - Be specific and constructive
   - Suggest improvements

4. **Request Changes or Approve**
   - "Request changes" if issues found
   - "Approve" if looks good
   - "Comment" for questions

**Review Checklist**:
- [ ] Content is accurate
- [ ] Links work
- [ ] Formatting is consistent
- [ ] No typos or grammar errors
- [ ] Follows project style guide
- [ ] Images/diagrams are clear

### Responding to Review Feedback

```bash
# 1. Make requested changes locally
# Edit files based on feedback

# 2. Commit changes
git add .
git commit -m "docs: address review feedback - add more examples"

# 3. Push to same branch
git push origin feature/add-troubleshooting-guide

# PR automatically updates!
```

**Responding to Comments**:
- Reply to each comment
- Mark as resolved when fixed
- Thank reviewers for feedback

### Merging Pull Requests

**Merge Strategies**:

1. **Create a Merge Commit** (default)
   - Preserves complete history
   - Shows when feature was merged
   - Best for: team projects

2. **Squash and Merge**
   - Combines all commits into one
   - Cleaner history
   - Best for: multiple small commits

3. **Rebase and Merge**
   - Linear history
   - No merge commits
   - Best for: maintaining clean timeline

**After Merging**:
```bash
# Delete feature branch (GitHub UI or):
git push origin --delete feature/add-troubleshooting-guide

# Update your local main
git checkout main
git pull origin main

# Delete local feature branch
git branch -d feature/add-troubleshooting-guide
```

---

## GitHub Features for Documentation

### GitHub Pages

**Publish documentation as a website**

**Setup**:

1. Go to repository Settings
2. Scroll to "Pages"
3. Select source:
   - Branch: `main`
   - Folder: `/docs` or `/ (root)`
4. Click "Save"

**Custom Domain** (optional):
```
# Add CNAME file to repository root
www.yourdomain.com
```

**Popular Static Site Generators**:
- **Jekyll**: Built into GitHub Pages
- **MkDocs**: Python-based, Material theme
- **Docusaurus**: React-based, from Facebook
- **VuePress**: Vue-based
- **Hugo**: Go-based, very fast

### GitHub Issues

**Track documentation tasks**

**Create Issue**:
```markdown
**Title**: Add deployment guide for AWS

**Description**:
We need a comprehensive guide for deploying to AWS.

Should include:
- [ ] EC2 setup
- [ ] S3 configuration
- [ ] CloudFront CDN
- [ ] SSL certificates

**Labels**: documentation, enhancement
**Assignee**: @username
**Milestone**: v2.0 Documentation
```

**Issue Templates**:

Create `.github/ISSUE_TEMPLATE/documentation.md`:

```markdown
---
name: Documentation Request
about: Suggest new or improved documentation
labels: documentation
---

## What documentation is needed?
Clear description of what needs to be documented

## Why is this needed?
Who will benefit and how

## Suggested content
Outline or draft if available

## Additional context
Links, examples, references
```

### GitHub Discussions

**Community conversations**

**Use for**:
- Q&A about documentation
- Feature requests
- General discussions
- Showcasing projects

**Enable**:
1. Repository Settings
2. Features → ✅ Discussions
3. Set up categories

### GitHub Projects

**Project management for documentation**

**Create Project**:
1. Projects tab → New project
2. Choose template (Board, Table, Roadmap)
3. Add cards for documentation tasks

**Example Board**:
```
To Do          In Progress       Done
────────       ────────────      ────────
□ API docs     ■ Install guide   ✓ README
□ FAQ          ■ Troubleshoot    ✓ License
□ Examples                       ✓ Contributing
```

### GitHub Actions (Automation)

**Automate documentation tasks**

**Example: Spell Check on PR**

Create `.github/workflows/spell-check.yml`:

```yaml
name: Spell Check

on: [pull_request]

jobs:
  spell-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Spell Check
        uses: rojopolis/spellcheck-github-actions@0.24.0
        with:
          source_files: '**/*.md'
```

**Example: Link Checker**

```yaml
name: Check Links

on:
  schedule:
    - cron: '0 0 * * 0'  # Weekly
  workflow_dispatch:

jobs:
  link-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Link Checker
        uses: lycheeverse/lychee-action@v1
        with:
          args: '--verbose --no-progress **/*.md'
```

**Example: Auto-deploy to GitHub Pages**

```yaml
name: Deploy Docs

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Setup Node
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Build
        run: |
          npm install
          npm run build

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

---

## Advanced Workflows

### Git Tags and Releases

**Create version tags**:

```bash
# Create tag
git tag -a v1.0.0 -m "Version 1.0.0 - Initial release"

# Push tag to GitHub
git push origin v1.0.0

# Push all tags
git push origin --tags

# List tags
git tag

# Delete tag
git tag -d v1.0.0
git push origin --delete v1.0.0
```

**Create GitHub Release**:

1. Go to Releases
2. Click "Create a new release"
3. Choose tag (or create new)
4. Add release notes
5. Attach files if needed
6. Publish release

### Git Hooks

**Automate local checks before commit**

Create `.git/hooks/pre-commit`:

```bash
#!/bin/sh
# Pre-commit hook: Check for TODO comments

if git diff --cached | grep -i "TODO"; then
    echo "Error: Found TODO comments. Please resolve before committing."
    exit 1
fi

# Spell check staged markdown files
git diff --cached --name-only --diff-filter=ACM | grep '.md$' | \
    xargs npx markdown-spellcheck -n -a --en-us

exit 0
```

Make executable:
```bash
chmod +x .git/hooks/pre-commit
```

### Git Submodules

**Include other repositories**

```bash
# Add submodule
git submodule add https://github.com/user/shared-docs.git docs/shared

# Clone repo with submodules
git clone --recursive <repository-url>

# Update submodules
git submodule update --remote --merge
```

### Git Worktrees

**Work on multiple branches simultaneously**

```bash
# Create worktree for different branch
git worktree add ../docs-v2 feature/version-2-docs

# List worktrees
git worktree list

# Remove worktree
git worktree remove ../docs-v2
```

---

## Best Practices

### Commit Message Guidelines

**Format**:
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types**:
- `docs`: Documentation changes
- `fix`: Fixing errors
- `update`: Updating existing content
- `add`: Adding new content
- `remove`: Removing content
- `refactor`: Reorganizing

**Examples**:

```bash
# Good commit messages
git commit -m "docs: add installation guide for Windows users"
git commit -m "fix: correct API endpoint URL in reference"
git commit -m "update: improve code examples in tutorial"

# Bad commit messages (avoid)
git commit -m "update"
git commit -m "fix stuff"
git commit -m "changes"
```

**Detailed Commit**:
```bash
git commit -m "docs: add comprehensive troubleshooting section

- Added common installation issues
- Included platform-specific solutions
- Added screenshots for clarity
- Updated table of contents

Closes #42"
```

### Documentation Versioning

**Strategy 1: Branches per Version**
```bash
# Create version branches
git checkout -b v1.x
git checkout -b v2.x

# Update specific version
git checkout v1.x
# make changes
git commit -m "docs: update v1.x installation guide"
```

**Strategy 2: Folders per Version**
```
docs/
├── v1/
│   ├── getting-started.md
│   └── api-reference.md
├── v2/
│   ├── getting-started.md
│   └── api-reference.md
└── latest/  # Symlink or copy
```

### Collaboration Guidelines

**Team Communication**:
- Use issues for tracking work
- Comment on PRs for discussions
- Use Discussions for Q&A
- Tag team members: `@username`

**Code Owners**:

Create `.github/CODEOWNERS`:
```
# Documentation team owns all docs
/docs/ @docs-team

# API docs require API team review
/docs/api-reference.md @api-team
```

**Branch Protection**:

Settings → Branches → Add rule:
- ✅ Require pull request reviews
- ✅ Require status checks to pass
- ✅ Require conversation resolution
- ✅ Do not allow bypassing

### Security Best Practices

**Never Commit**:
- ❌ API keys or tokens
- ❌ Passwords
- ❌ Private keys
- ❌ Personal information
- ❌ Internal URLs

**If Accidentally Committed**:
```bash
# Remove from history (use with caution)
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch path/to/file" \
  --prune-empty --tag-name-filter cat -- --all

# Or use BFG Repo-Cleaner (easier)
bfg --delete-files secret-file.txt
git reflog expire --expire=now --all
git gc --prune=now --aggressive
```

**Better**: Use GitHub's secret scanning and immediately rotate exposed credentials.

### Markdown Consistency

**Style Guide**:
- Use consistent heading levels
- One sentence per line (easier diffs)
- Consistent code block formatting
- Use reference-style links for readability
- Keep line length reasonable (80-120 chars)

**Example**:
```markdown
<!-- Good: One sentence per line -->
This is the first sentence.
This is the second sentence.
It makes diffs clearer.

<!-- Bad: Long wrapped lines -->
This is the first sentence. This is the second sentence. It makes diffs harder to read when changes span multiple sentences in one line.
```

---

## Troubleshooting

### Common Issues

**Issue**: "Permission denied (publickey)"
```bash
# Solution: Check SSH key setup
ssh -T git@github.com

# If fails, regenerate and add SSH key (see SSH Key Setup)
```

**Issue**: "Merge conflict"
```bash
# Solution: Resolve conflicts manually
git status  # See conflicted files
# Edit files to resolve
git add resolved-file.md
git commit
```

**Issue**: "Detached HEAD state"
```bash
# Solution: Create branch from current state
git checkout -b recovery-branch
# Or return to main
git checkout main
```

**Issue**: "Remote already exists"
```bash
# Solution: Update existing remote
git remote set-url origin git@github.com:new-url.git

# Or remove and re-add
git remote remove origin
git remote add origin git@github.com:new-url.git
```

### Getting Help

**Git Help**:
```bash
# Get help for command
git help <command>
git help commit

# Quick reference
git <command> --help
```

**GitHub CLI Help**:
```bash
gh help
gh pr --help
```

**Resources**:
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)
- [Pro Git Book](https://git-scm.com/book)
- [GitHub Skills](https://skills.github.com/)

---

## Quick Reference

### Common Commands Cheat Sheet

```bash
# Setup
git config --global user.name "Name"
git config --global user.email "email@example.com"

# Start
git init                    # New repository
git clone <url>            # Copy repository

# Daily workflow
git status                 # Check status
git add <file>             # Stage file
git add .                  # Stage all
git commit -m "message"    # Commit
git push                   # Upload
git pull                   # Download

# Branching
git branch                 # List branches
git branch <name>          # Create branch
git checkout <name>        # Switch branch
git checkout -b <name>     # Create and switch
git merge <branch>         # Merge branch

# History
git log                    # View history
git log --oneline          # Compact history
git diff                   # See changes
git show <commit>          # Show commit

# Undo
git checkout -- <file>     # Discard changes
git reset HEAD <file>      # Unstage
git revert <commit>        # Revert commit
```

---

**Last Updated**: October 17, 2025
**Version**: 1.0
