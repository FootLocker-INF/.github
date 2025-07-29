
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
<summary>Branch Structure</summary> 

### Branch Management
- 🔄 Keep branches short-lived (< 2 weeks)
- 🧹 Delete merged branches promptly
- 📝 Use descriptive branch names
- 🔄 Regularly sync with parent branch
- 🚫 Avoid long-running feature branches

  ### Main Branches

  #### `main`
  - **Purpose**: Production-ready code that is stable and deployable
  - **Protection**: Protected branch with strict merge requirements
  - **Deployment**: Automatically deployed to production environment
  - **Merge Policy**: Only accepts merges from `hotfix/*` and `develop` branches
  - **Naming Convention**: `main`

#### `develop`
- **Purpose**: Integration branch where all features come together
- **Status**: Contains the latest development changes for the next release
- **Testing**: Continuous integration runs on every commit
- **Merge Policy**: Accepts merges from `feature/*` and `bugfix/*` branches
- **Naming Convention**: `develop`

### Supporting Branches

#### Feature Branches (`feature/*`)
- **Purpose**: Development of new features and enhancements
- **Lifetime**: Created from `develop`, merged back to `develop`
- **Naming Convention**: `feature/JIRA-123-description` or `feature/short-description`
- **Examples**:
  - `feature/USER-456-user-authentication`
  - `feature/API-789-payment-integration`
  - `feature/dashboard-redesign`
    
</details>


<details>
  <summary>Branch Protection Rules</summary>
 
### `main` Branch
- ✅ Require pull request reviews (minimum 2 approvers)
- ✅ Require status checks to pass
- ✅ Require branches to be up to date before merging
- ✅ Restrict pushes that create merge commits
- ✅ Require administrator approval for emergency changes
- ❌ Allow force pushes
- ❌ Allow deletions

### `develop` Branch
- ✅ Require pull request reviews (minimum 1 approver)
- ✅ Require status checks to pass
- ✅ Require branches to be up to date before merging
- ❌ Allow force pushes
- ❌ Allow deletions


## Code Review Guidelines

### For Authors
- ✅ Write clear, descriptive commit messages
- ✅ Keep pull requests focused and reasonably sized
- ✅ Add tests for new functionality
- ✅ Update documentation when necessary
- ✅ Self-review your code before requesting review
- ✅ Respond to feedback promptly and professionally


## Continuous Integration

### Required Checks
- ✅ Unit tests pass
- ✅ Integration tests pass
- ✅ Code coverage meets threshold (minimum 80%)
- ✅ Linting passes
- ✅ Security scan passes
- ✅ Build succeeds

### Environment Deployment

| Branch | Environment | Trigger | Access |
|--------|-------------|---------|--------|
| `main` | Production | Automatic on merge | Public |
| `develop` | Staging | Automatic on merge | Internal team |
| `feature/*` | Development | Manual or on push | Developers |

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
  <summary>Code Quality & Best Practices</summary>

### Code Quality
- 📝 Write meaningful commit messages
- 🧪 Include tests with new features
- 📚 Update documentation
- 🔍 Run local tests before pushing
- 🏃‍♂️ Keep pull requests focused

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

*Last updated: July 24, 2025*
*Version: 1.0*

---
