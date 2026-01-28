# Git Branching Workflow Demo

This repository demonstrates a professional Git branching strategy for module-based development.

## 📋 Branching Strategy Overview

### Branch Hierarchy
```
main (production)
├── feature/auth-module
│   ├── auth/login-api
│   ├── auth/signup-ui
│   └── auth/password-reset
├── feature/payment-module
│   ├── payment/razorpay-integration
│   └── payment/history-api
└── feature/user-profile-module
    ├── user-profile/model
    ├── user-profile/api
    └── user-profile/frontend
```

## 🚀 Quick Start Guide

### 1. Clone the Repository
```bash
git clone https://github.com/akashBv6680/branching-workflow-demo.git
cd branching-workflow-demo
```

### 2. View All Branches
```bash
git branch -a
```

## 📝 Workflow Steps

### Step 1: Create Feature Branch from Main
```bash
# Update main
git checkout main
git pull origin main

# Create feature branch
git checkout -b feature/auth-module
git push -u origin feature/auth-module
```

### Step 2: Create Development Sub-Branches
```bash
# From feature branch, create sub-branch for specific task
git checkout feature/auth-module
git pull origin feature/auth-module

# Create sub-branch
git checkout -b auth/login-api
```

### Step 3: Development Work
```bash
# Make your code changes
# Add files
git add .

# Commit with meaningful message
git commit -m "Implement login API endpoint with JWT authentication"

# Push to remote
git push -u origin auth/login-api
```

### Step 4: Merge Sub-Branch to Feature Branch
```bash
# Update from feature branch
git checkout auth/login-api
git pull origin feature/auth-module

# Run tests
pytest tests/

# Push final changes
git push origin auth/login-api

# Create Pull Request: auth/login-api → feature/auth-module
# Get code review and approval
# Merge PR on GitHub
```

### Step 5: Merge Feature Branch to Main
```bash
# After all sub-branches are merged and tested
git checkout feature/auth-module
git pull origin main

# Resolve any conflicts
# Run full test suite
pytest

# Create Pull Request: feature/auth-module → main
# Get approval
# Merge to main
```

## 🌳 Complete Example: User Profile Module

### 1. Create Feature Branch
```bash
git checkout main
git pull origin main
git checkout -b feature/user-profile-module
git push -u origin feature/user-profile-module
```

### 2. Create Sub-Branches and Develop

**Database Models:**
```bash
git checkout feature/user-profile-module
git checkout -b user-profile/model
# Create models, migrations
git add .
git commit -m "Add User Profile model and migrations"
git push -u origin user-profile/model
# PR → feature/user-profile-module
```

**API Endpoints:**
```bash
git checkout feature/user-profile-module
git pull origin feature/user-profile-module
git checkout -b user-profile/api
# Create CRUD APIs
git add .
git commit -m "Add User Profile CRUD APIs"
git push -u origin user-profile/api
# PR → feature/user-profile-module
```

**Frontend UI:**
```bash
git checkout feature/user-profile-module
git pull origin feature/user-profile-module
git checkout -b user-profile/frontend
# Create UI components
git add .
git commit -m "Add User Profile UI components"
git push -u origin user-profile/frontend
# PR → feature/user-profile-module
```

### 3. Final Merge to Main
```bash
git checkout feature/user-profile-module
git pull origin main
# Test everything
# PR → main
```

## ✅ Best Practices

1. **Always pull before creating new branches**
   ```bash
   git checkout main
   git pull origin main
   ```

2. **Use descriptive branch names**
   - Feature: `feature/module-name`
   - Sub-branch: `module-name/specific-task`

3. **Write meaningful commit messages**
   ```bash
   git commit -m "Add login endpoint with email validation"
   ```

4. **Keep branches up-to-date**
   ```bash
   git pull origin feature/auth-module
   ```

5. **Run tests before merging**
   ```bash
   pytest tests/
   ```

6. **Use Pull Requests for code review**

7. **Delete merged branches**
   ```bash
   git branch -d auth/login-api
   git push origin --delete auth/login-api
   ```

## 📊 Branch Status Checklist

Use this for each module:

- [ ] Feature branch created from main
- [ ] Sub-branches created for each task
- [ ] Code developed and tested locally
- [ ] PR created and reviewed
- [ ] Sub-branch merged to feature branch
- [ ] Feature branch tested completely
- [ ] Feature branch merged to main
- [ ] Branches cleaned up

## 🔧 Useful Git Commands

```bash
# View current branch
git branch

# View all branches (local + remote)
git branch -a

# Switch to existing branch
git checkout branch-name

# Create and switch to new branch
git checkout -b new-branch-name

# Update current branch from remote
git pull origin branch-name

# Push current branch
git push origin branch-name

# Delete local branch
git branch -d branch-name

# Delete remote branch
git push origin --delete branch-name

# View commit history
git log --oneline --graph --all

# Check status
git status
```

## 🎯 Real Project Workflow

When your senior adds you as collaborator:

1. **Clone the project**
2. **Create feature branch for your module**
3. **Break module into sub-tasks**
4. **Create sub-branch for each task**
5. **Develop → Test → Push → PR**
6. **Merge sub-branches to feature**
7. **Merge feature to main after approval**

---

**Repository Owner:** akashBv6680  
**Purpose:** Git workflow demonstration and practice
