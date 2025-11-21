# Migration Guide for Pending Features

This guide covers the pending pull requests that introduce new features and changes to Claude Code. These features are currently under review and will require migration steps once merged.

---

## PR #53: Automate Docker Image Builds with GitHub Actions

**Status**: Open  
**Author**: ryan-leu  
**Branch**: pr/2466-QwertyJack-main

### Summary of Changes
This PR introduces automated Docker image building through GitHub Actions CI/CD pipeline. The workflow automatically triggers on branch updates to ensure Docker images stay synchronized with the latest codebase.

### Key Features
- **Automated Build Pipeline**: GitHub Actions workflow for continuous Docker image building
- **Template-Based**: Uses GitHub Action templates following best practices
- **Automatic Triggers**: Runs on every push event to the branch

### Configuration Changes
**New Files**:
- `.github/workflows/docker-build.yml` (or similar) - GitHub Actions workflow configuration

### Installation/Usage
Once merged, Docker images will be automatically built when:
1. Code is pushed to the configured branch
2. Pull requests are created/updated
3. The workflow can be manually triggered from the Actions tab

**No user action required** - the workflow runs automatically in the background.

### Migration Steps
1. After merge, check the GitHub Actions tab to verify workflow execution
2. Docker images will be available in the configured container registry
3. Update local documentation to reference automated build process
4. Consider adding workflow status badges to README

### Environment Variables
Check the workflow file for any required secrets:
- Container registry credentials (if pushing to external registry)
- GitHub token (usually auto-provided by GitHub Actions)

---

## PR #52: Shell Completions (bash, zsh, fish)

**Status**: Open  
**Author**: ryan-leu  
**Branch**: pr/4943-gitmpr-feat/shell-completion-scripts

### Summary of Changes
Adds static tab-autocompletion scripts for the Claude CLI across multiple shell environments. This enhances developer experience by providing command-line tab completion.

### Key Features
- **Multi-Shell Support**: Completions for bash, zsh, and fish
- **Static Scripts**: Pre-built completion files in `shell-completions/` directory
- **User-Friendly**: Simple sourcing mechanism for activation

### New Files
- `shell-completions/claude-completions.bash` - Bash completion script
- `shell-completions/claude-completions.zsh` - Zsh completion script  
- `shell-completions/claude-completions.fish` - Fish shell completion script

### Installation Instructions

#### For Bash Users
```bash
# Add to your ~/.bashrc or ~/.bash_profile
source /path/to/claude-code/shell-completions/claude-completions.bash
```

#### For Zsh Users
```bash
# Add to your ~/.zshrc
source /path/to/claude-code/shell-completions/claude-completions.zsh
```

#### For Fish Users
```bash
# Copy to Fish completions directory
cp /path/to/claude-code/shell-completions/claude-completions.fish ~/.config/fish/completions/
```

### Usage After Installation
Once sourced, use TAB key to autocomplete:
- Claude commands
- Command options and flags
- File paths
- Available arguments

### Migration Notes
**Important**: The PR notes that upstream integration isn't possible because Claude Code is not open source. Users must manually source these completion files.

**Ideal vs. Current Approach**:
- **Ideal** (not available): `source <(claude completion $SHELL)`
- **Current** (manual): Source the appropriate static file for your shell

### Limitations
- Completions are static and may require updates when new commands are added
- Cannot be generated dynamically from the binary
- Must be manually maintained in sync with CLI changes

---

## PR #51: Enhanced Statsig Event Logging in GitHub Workflows

**Status**: Open  
**Author**: ryan-leu  
**Branch**: pr/5435-alokdangre-demo

### Summary of Changes
Enhances telemetry and analytics by adding additional Statsig event logging for GitHub workflow operations, particularly around issue management lifecycle events.

### Key Features
- **Extended Event Logging**: Captures duplicate issue closures and comment additions
- **Consistency Improvements**: Aligns with existing logging patterns
- **Better Analytics**: Provides more granular data for issue management insights

### New Event Types
The following events are now logged to Statsig:
1. **Issue Closed as Duplicate**: When an issue is marked as duplicate and closed
2. **Duplicate Comment Added**: When a duplicate-marking comment is added to an issue
3. Additional issue lifecycle events (check workflow changes for complete list)

### Configuration Changes
**Modified Files**:
- GitHub workflow files in `.github/workflows/` directory
- Statsig logging integration points

### Environment Variables/Secrets Required
May require Statsig configuration:
- `STATSIG_API_KEY` or similar authentication token
- Statsig project/environment identifiers

### Migration Steps
1. **Verify Statsig Configuration**: Ensure Statsig credentials are configured in repository secrets
2. **Review Event Schema**: Check that your Statsig dashboard is configured to receive new event types
3. **Update Dashboards**: Create or update Statsig dashboards to visualize new metrics
4. **Test Workflow**: Trigger test events to verify logging is working correctly

### Usage
No direct user action required - the logging happens automatically within GitHub Actions workflows when:
- Issues are closed
- Duplicate status is assigned
- Comments are added to issues

### Data Privacy Considerations
- Review what data is being sent to Statsig
- Ensure compliance with privacy policies
- Consider PII in issue descriptions/comments

---

## General Migration Checklist

When these PRs are merged, repository administrators should:

- [ ] Review and approve GitHub Actions workflows
- [ ] Configure necessary secrets and environment variables
- [ ] Update repository documentation (README, CONTRIBUTING)
- [ ] Test Docker build automation (PR #53)
- [ ] Distribute shell completion installation instructions (PR #52)
- [ ] Verify Statsig event logging (PR #51)
- [ ] Update CHANGELOG with merged features
- [ ] Announce changes to repository contributors

## Support and Questions

For questions about these pending features:
1. Comment on the respective pull request
2. Check PR description for additional context
3. Review linked issues or related discussions
4. Contact PR author for clarification

---

*Last Updated: 2025-11-21*  
*Generated from open pull requests in ryan-leu/claude-code*
