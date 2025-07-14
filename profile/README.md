

# Welcome to FootLocker-INF on GitHub 👋

This page provides essential information and guidelines for working within our GitHub organization.

---
## 🔐 GitHub Access
Access is managed via teams. Request access through
[Github Onboarding](https://footlocker.atlassian.net/wiki/spaces/Observabil/pages/107349801/GitHub+Onboarding) or contact an admin.

## 🤖 GitHub Copilot
Copilot is available for approved users. Learn how to enable and use it in our
[Github Copilot Guide](https://footlocker.atlassian.net/wiki/spaces/Observabil/pages/107349859/GitHub+Copilot)

## 🚀 Getting Started
New here? Start here [Getting Started](https://footlocker.sharepoint.com/:w:/s/ITAutomationandToolsEngineering/ETlF9axeDgxItYTAYb_LVIYB42WF1yQfBNllWuVagCvhUg?e=JScOL4) to set up your environment and understand our workflows.


## 📛 Naming Standards
### In Progress


## 🏷️ Tagging
Tag synchronization is handled automatically by a script that runs as part of our deployment or data processing pipeline. This script is responsible for identifying relevant resources, applying or updating tags based on predefined rules or metadata sources, and ensuring consistency across environments.	

| Name | Description | |
| --- | --- | ---|
| Application | Github Footlocker-INF | |
| Environment | Dev & Prod | |
| Teams | Cloud Eng, Cloud Team, DBA Team, DevOps Eng, IT Automation, Network Eng, Platform Eng | |
| RepoOwner | Cloud Eng, Cloud Team, DBA Team, DevOps Eng, IT Automation, Network Eng, Platform Eng | |
| Repositories | [Footlocker-INF Repos](https://github.com/orgs/FootLocker-INF/repositories?) | |
| Criticality | High, Medium, Low | |


## Branch Structure

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

**Workflow**:
1. Create from `develop` branch
2. Develop and test the feature
3. Create pull request to `develop`
4. Code review and approval required
5. Merge to `develop` and delete feature branch

#### Bugfix Branches (`bugfix/*`)
- **Purpose**: Fix bugs found in the `develop` branch or during testing
- **Lifetime**: Created from `develop`, merged back to `develop`
- **Naming Convention**: `bugfix/JIRA-123-description` or `bugfix/short-description`
- **Examples**:
  - `bugfix/BUG-456-login-validation`
  - `bugfix/API-789-null-pointer-exception`
  - `bugfix/ui-responsive-issues`

**Workflow**:
1. Create from `develop` branch
2. Fix the bug and add tests
3. Create pull request to `develop`
4. Code review and testing required
5. Merge to `develop` and delete bugfix branch

#### Hotfix Branches (`hotfix/*`)
- **Purpose**: Urgent fixes for critical issues in production
- **Lifetime**: Created from `main`, merged to both `main` and `develop`
- **Priority**: Highest priority - bypasses normal development cycle
- **Naming Convention**: `hotfix/version-description` or `hotfix/critical-issue`
- **Examples**:
  - `hotfix/v1.2.1-security-vulnerability`
  - `hotfix/v1.2.1-payment-gateway-failure`
  - `hotfix/critical-database-connection`

**Workflow**:
1. Create from `main` branch
2. Fix the critical issue
3. Update version number if applicable
4. Create pull request to `main`
5. After merge to `main`, merge to `develop`
6. Deploy to production immediately
7. Delete hotfix branch

## Branch Protection Rules

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

### For Reviewers
- ✅ Review within 24 hours (48 hours maximum)
- ✅ Check for code quality, security, and performance
- ✅ Verify tests are adequate and passing
- ✅ Ensure documentation is updated
- ✅ Provide constructive feedback
- ✅ Approve when satisfied with changes

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

## Emergency Procedures

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

## Best Practices

### Branch Management
- 🔄 Keep branches short-lived (< 2 weeks)
- 🧹 Delete merged branches promptly
- 📝 Use descriptive branch names
- 🔄 Regularly sync with parent branch
- 🚫 Avoid long-running feature branches

### Merge Strategies
- **Feature/Bugfix to Develop**: Squash and merge
- **Develop to Main**: Create merge commit
- **Hotfix**: Create merge commit to preserve history

### Code Quality
- 📝 Write meaningful commit messages
- 🧪 Include tests with new features
- 📚 Update documentation
- 🔍 Run local tests before pushing
- 🏃‍♂️ Keep pull requests focused

## Troubleshooting

### Common Issues

**Merge Conflicts**
```bash
# Resolve conflicts in affected files
git add <resolved-files>
git commit -m "resolve: merge conflicts"
```

**Outdated Branch**
```bash
# Update feature branch with latest develop
git checkout feature/my-feature
git rebase develop
# or
git merge develop
```

**Accidental Commit to Wrong Branch**
```bash
# Move commits to correct branch
git checkout correct-branch
git cherry-pick <commit-hash>
git checkout wrong-branch
git reset --hard HEAD~1
```

## Tools and Integrations

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

*Last updated: July 2, 2025*
*Version: 1.0*

---
