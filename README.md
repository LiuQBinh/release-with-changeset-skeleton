# 🚀 Release with Changeset Skeleton

A skeleton for implementing changeset-based release management.

## 📋 Overview

Automated release workflow using [Changesets](https://github.com/changesets/changesets) and GitHub Actions.

## ⚙️ GitHub Actions Workflows

1. **🔍 check-bump-file**: Verifies bump files in `.changeset` directory
   - Runs on PRs
   - Fails if no changeset files found

2. **🚀 release**: Creates release on main branch push
   - Creates "Version Packages" PR
   - Updates versions based on changesets

## 📝 Release Process

### Steps to development
1. 📦 Create changeset:
   ```bash
   npx changeset add
   ```
   - Select change type (patch/minor/major)
   - Add change description

2. 💾 Commit and push your bump files
   - Required for PR approval
   - <span style="color: red">`check-bump-file` will block merge if missing</span>
   
   Example content of bump files:
   ```markdown:.changeset/rare-coins-sneeze.md
   ---
   "release-with-changeset-skeleton": patch
   ---
   
   Test
   ```

### Steps to release
1. 🔄 Create PR → `check-bump-file` verifies changesets
2. 📤 Merge to main → `release` creates "Version Packages" PR
3. 🎉 Merge "Version Packages" PR → creates release
