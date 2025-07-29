
# Welcome to FootLocker-ORG_NAME on GitHub 👋

This page provides essential information and guidelines for working within our GitHub organization.

---
## 🔐 GitHub Access
Access is managed via teams. Request access through
[Github Access](https://footlocker.atlassian.net/wiki/spaces/PEP/pages/452624578/GitHub+Access) or contact an admin.

<details>
<summary> Virtual Studio Code Setup: </summary>

 In progress..
Here is the steps if needing to setup guthub to VSC....

</details>

## 🤖 GitHub Copilot
Copilot is available for approved users. Learn how to enable and use it in our
[Github Copilot Guide](https://footlocker.atlassian.net/wiki/spaces/Observabil/pages/107349859/GitHub+Copilot)


## 📛 Naming Standards
### In Progress


## 🏷️ Tagging

[Leanix](https://footlocker.leanix.net/footlockerproduction/dashboard/aca7bb56-4b03-4813-8688-ae7d01db71a5)

Tag synchronization is handled automatically by a script that runs as part of our deployment or data processing pipeline. This script is responsible for identifying relevant resources, applying or updating tags based on predefined rules or metadata sources, and ensuring consistency across environments.	

<details>
<summary> Orgs & Teams: </summary>
 When creating teams, it's helpful to use acronyms in the team names to make it easier to identify and filter them.
<details>
<summary>Examples:</summary>
Org Names:
 
- Customer Experience → Footlocker-CE
- Infrastructure → Footlocker-Infrastructure
- Core Retail → Footlocker-CR
- Data Analytics → Footlocker-DA
  
This naming convention improves clarity and consistency across platforms.

<summary>Examples:</summary>

Team Names:
 
- Platform Engineering
- Cloud Engineering
- IT Automation
  
</details>
</details>
</details>

<details>
<summary>Enterprise Owners:</summary>
 
- Satya Prakash
- Ryan siegel
- Austtin Poindexter
- Dani Tam
- Jake francois
  
[Footlocker-INF Repos](https://github.com/orgs/FootLocker-INF/repositories?)

</details>

 ## :page_with_curl: More Information

 
<details>
<summary>Branching Flow & Structure</summary> 

### Best Practices for Git Branching: A Detailed Guide

Effective branching strategies are crucial for maintaining code quality, collaboration, and productivity in Git-based projects. This document outlines **best practices for branching**, **common issues**, and their **solutions**.

---

## **1. Best Practices for Git Branching**

### 1.1. **Adopt a Clear Branching Strategy**
Choose a strategy that aligns with your team's size, workflow, and release schedule. Popular branching models include:

- **Git Flow**:
  - Use `main` for production-ready code.
  - Use `develop` for integrating completed features.
  - Feature branches (`feature/*`), release branches (`release/*`), and hotfix branches (`hotfix/*`) for specific tasks.

- **GitHub Flow**:
  - Use `main` for production-ready code.
  - Create short-lived feature branches for individual tasks.
  - Merge feature branches into `main` after approval via pull requests.

- **Trunk-Based Development**:
  - Maintain a single `main` branch with frequent commits.
  - Use short-lived branches for features, merging them into `main` quickly.

### 1.2. **Keep Branches Short-Lived**
- Avoid long-lived feature branches to prevent merge conflicts.
- Merge frequently to ensure the branch stays up-to-date with the base branch (e.g., `main` or `develop`).

### 1.3. **Use Meaningful Branch Names**
- Use a consistent naming convention to make branch purposes clear.
- Examples:
  - `feature/login-page`
  - `bugfix/fix-login-error`
  - `hotfix/security-vulnerability`
  - `release/v1.0.0`

### 1.4. **Commit Frequently, but Meaningfully**
- Commit small, logical changes to improve collaboration and avoid losing work.
- Write meaningful commit messages that describe the changes (e.g., "Add login functionality" instead of "fix").

### 1.5. **Regularly Sync with the Base Branch**
- Frequently merge or rebase the base branch (`main` or `develop`) into your feature branch to stay updated.
- Use:
  ```bash
  git pull origin main
  ```

### 1.6. **Protect Critical Branches**
- Enable branch protection rules for `main` or `develop` branches to prevent direct commits or accidental deletions.
- Require pull requests and code reviews before merging.

### 1.7. **Automate with CI/CD Pipelines**
- Use CI/CD pipelines to automatically test and validate code changes when pushing to branches.

### 1.8. **Define a Merge Strategy**
- Use **Squash and Merge** for cleaner commit history in `main`.
- Use **Rebase and Merge** for linear commit history.
- Avoid using **Merge Commits** unless retaining branch history is important.

---

## **2. Common Issues and Their Solutions**

### 2.1. **Merge Conflicts**
**Issue**: Conflicts occur when changes in two branches affect the same lines in a file or nearby lines.

**Solutions**:
1. **Resolve Conflicts Locally**:
   - Open conflicting files, resolve conflicts, and remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
   - Add resolved files and commit:
     ```bash
     git add <file>
     git commit
     ```

2. **Prevent Conflicts**:
   - Regularly pull changes from the base branch.
   - Communicate with team members about concurrent changes to avoid overlapping work.

---

### 2.2. **Forgotten Branch Merges**
**Issue**: Feature branches are abandoned or forgotten without being merged.

**Solutions**:
1. Use the `git branch` command to list and clean up stale branches:
   ```bash
   git branch -d <branch-name>
   git branch -D <branch-name> # Force delete if unmerged
   ```

2. Enable pull request workflows to ensure all branches are reviewed and merged appropriately.

---

### 2.3. **Large Divergences Between Branches**
**Issue**: Long-lived branches diverge significantly, making merging difficult.

**Solutions**:
1. Rebase frequently:
   ```bash
   git rebase main
   ```

2. Break work into smaller, incremental changes and merge more often.

---

### 2.4. **Unclear Branch Purpose**
**Issue**: Ambiguously named branches confuse team members about their purpose.

**Solutions**:
1. Establish and enforce a branch naming convention.
2. Use descriptive names like:
   - `feature/add-payment-gateway`
   - `bugfix/ui-overlap-issue`

---

### 2.5. **Accidental Pushes to the Wrong Branch**
**Issue**: Developers accidentally push changes directly to `main` or another protected branch.

**Solutions**:
1. **Enable Branch Protection Rules**:
   - Disallow direct commits and require pull requests for `main` and other critical branches.

2. **Undo an Accidental Push**:
   - If you accidentally push, reset the branch to its previous state:
     ```bash
     git reset --hard origin/main
     git push --force
     ```

---

### 2.6. **Deleted or Lost Branches**
**Issue**: A branch is accidentally deleted.

**Solutions**:
1. Recover a Deleted Branch:
   ```bash
   git reflog
   git checkout -b <branch-name> <commit-hash>
   ```

2. Use remote backups if the branch was pushed to a remote repository.

---

### 2.7. **Branch Bloat**
**Issue**: Too many branches accumulate, cluttering the repository.

**Solutions**:
1. Regularly delete merged or unused branches:
   ```bash
   git branch -d <branch-name>
   git branch -D <branch-name> # Force delete
   ```

2. Use automation tools to identify stale branches.

---

## **3. Additional Best Practices**

### 3.1. **Use Feature Toggles**
- For incomplete or experimental features, use feature flags instead of long-lived feature branches. This reduces branching overhead and allows code integration without affecting users.

### 3.2. **Document the Workflow**
- Create a branching workflow document to standardize processes across the team.

### 3.3. **Encourage Frequent Communication**
- Discuss branch changes and status updates in daily standups or team meetings to ensure everyone is aligned.

---
</details>

<details>
  <summary>Code Quality & Best Practices</summary>

### Code Quality
- 📝 Write meaningful commit messages
  ✅ Good Example:
  ```bash
  git commit -m "fix(auth): handle token expiration and refresh automatically" 

 🚫 Bad Example:
  ```bash
  git commit -m "fix stuff"
  ```
 
- 🧪 Include tests with new features
  ✅ Example
  ```bash
  describe('UserService', () => {
  it('should return user data when ID is valid', async () => {
    const user = await getUserById('123');
    expect(user.name).toBe('Alice');
  });
  });
  
- 📚 Update documentation
  ✅ Example: Update README.md or inline comments when:

 Adding new environment variables
  Changing API endpoints
  Modifying CLI commands
  ```bash

### New Environment Variable
`FEATURE_FLAG_NEW_UI=true`  
Enables the new user interface for beta testing.
```
- 🔍 Run local tests before pushing
  ✅ Example:
    ```bash
  # Run all tests
  npm test

  # Run linter
  npm run lint

  # Run type checks
  tsc --noEmit
- 🏃‍♂️ Keep pull requests focused
  
  ✅ Good PR:

  Adds password reset functionality with backend API and frontend form.

  🚫 Bad PR:

  Adds password reset, updates navbar, refactors login, and fixes unrelated bug.

</details>

 <details>
<summary>Git Pull & Push Guide</summary>
  

## 🔧 Prerequisites
- Git installed on your machine
- Access to a Git repository (e.g., GitHub, GitLab, Bitbucket)
- SSH or HTTPS access configured

---

## 📥 How to Pull Code

Pulling code means fetching the latest changes from a remote repository and merging them into your local branch.

### Steps:
1. **Navigate to your project directory**:
   ```bash
   cd /path/to/your/project
   ```
</details>


<details>
  <summary>Emergency Procedures</summary>
 
### Critical Production Issue
1. **Immediate Response**: Create hotfix branch from `main`
2. **Fast Track**: Bypass normal review process if necessary
3. **Communication**: Notify team leads and stakeholders
4. **Documentation**: Document the issue and resolution
5. **Post-Mortem**: Schedule retrospective to prevent recurrence

### Rollback Procedure
1. **Identify**: Determine the last known good commit
2. **Revert**: Create revert commit or hotfix
3. **Deploy**: Follow hotfix deployment process
4. **Monitor**: Verify system stability
5. **Investigate**: Analyze root cause offline

</details>

<details>
  <summary>Tools and Integrations</summary>
 
### Recommended Tools
- **Git GUI**: GitKraken, Sourcetree, or VS Code Git integration
- **Code Review**: GitHub/GitLab pull requests
- **CI/CD**: GitHub Actions, GitLab CI, Jenkins
- **Branch Protection**: Built-in repository settings

### Useful Git Aliases
```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```
---

</details>

*Last updated: July 29, 2025*
*Version: 1.0*

---
