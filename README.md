# Release with Changeset Skeleton

This project provides a skeleton for implementing changeset-based release management in your projects.

## Overview

This skeleton implements an automated release workflow using [Changesets](https://github.com/changesets/changesets) and GitHub Actions. It helps manage versioning and releases in a structured way.

## GitHub Actions Workflows

The project includes two main GitHub Actions workflows:

1. **check-bump-file**: Verifies the presence of bump files in the `.changeset` directory
   - Runs on pull requests
   - Ensures all changes are properly documented with changesets
   - Fails if no changeset files are found

2. **release**: Creates a new release when changes are pushed to the main branch
   - Triggers on push to main
   - Creates a "Version Packages" pull request
   - Updates version numbers based on changeset files

## Release Process

### Development Phase

1. Run the following command to create a new changeset:
   ```bash
   npx changeset add
   ```
   This will:
   - Prompt you to select the type of change (patch, minor, major)
   - Create a bump file in the `.changeset` directory
   - Allow you to add a description of your changes

2. Commit the generated bump files and push to main

### Release Phase

1. Create a new pull request
   - The `check-bump-file` workflow will automatically run to verify the presence of bump files
   - This ensures all changes are properly documented

2. Merge the pull request into main
   - The `release` workflow will trigger
   - A new "Version Packages" pull request will be created automatically
   - This PR will contain version updates based on your changeset files

3. Review and merge the "Version Packages" pull request
   - This will create the actual release
   - The release version will be determined by the bump files
   - After merging, the new version will be published
