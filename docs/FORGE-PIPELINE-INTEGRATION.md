# GitHub Forge Pipeline Integration

This document describes how to automatically update GitHub Forge Pipeline when work is completed.

## Current Manual Process

When completing work on a project tracked in Forge Pipeline:

1. **Create completion issue** in `harkers/github-forge-pipeline`:
   ```bash
   gh issue create --repo harkers/github-forge-pipeline \
     --title "[GFP-<WORKSTREAM>-<INITIATIVE>-<NUM>] <Description>" \
     --label "workstream:<ws>,priority:<p>,type:<t>,status:done" \
     --body "## Summary\n<summary>\n\n## Status\n✅ COMPLETED\n\n## Implementation\n<details>"
   ```

2. **Add to project:**
   ```bash
   gh project item-add 2 --owner harkers --url <issue-url>
   ```

3. **Close issue with summary:**
   ```bash
   gh issue close <num> --repo harkers/github-forge-pipeline \
     --comment "Completed. <summary>"
   ```

4. **Update tracking issue** with progress comment.

## Automation Options

### Option 1: Git Hooks (Recommended)

Create a post-commit hook that:
- Detects commit messages with `[GFP-XXX-XXX-NNN]` prefix
- Automatically creates/updates issues

**Hook location:** `.git/hooks/post-commit`

```bash
#!/bin/bash
# Extract GFP code from commit message
GFP_CODE=$(git log -1 --format='%s' | grep -oE '\[GFP-[A-Z]+-[A-Z]+-[0-9]+\]')

if [ -n "$GFP_CODE" ]; then
  # Would need GitHub API integration
  echo "Forge Pipeline reference detected: $GFP_CODE"
  echo "Manual sync recommended: gh issue comment ..."
fi
```

### Option 2: OpenClaw Skill

Create a skill that:
- Monitors workspace for commits
- Detects completion markers (commit messages, merged PRs)
- Updates Forge Pipeline automatically

**Skill file:** `~/.openclaw/workspace/skills/forge-pipeline-sync/SKILL.md`

### Option 3: GitHub Actions

Create a workflow in the project repo that:
- Triggers on push to main
- Calls Forge Pipeline API to create/update issues
- Requires Forge Pipeline API endpoint

## Recommended Workflow

For now, use this manual checklist after completing work:

```markdown
## Completion Checklist

- [ ] Code committed and pushed
- [ ] Forge submodule updated (if applicable)
- [ ] GitHub Forge Pipeline issue created
- [ ] Issue added to project
- [ ] Issue closed with completion summary
- [ ] Tracking issue updated
```

## Future Automation

A dedicated OpenClaw skill (`forge-pipeline-sync`) can automate this:

1. **Triggers:**
   - Commit with `[GFP-XXX]` reference
   - `/forge-complete` command in chat
   - Merged PR to tracked repo

2. **Actions:**
   - Parse commit/PR details
   - Create or update Forge Pipeline issue
   - Add to project with correct fields
   - Post completion summary

3. **Skill location:**
   ```
   ~/.openclaw/workspace/skills/forge-pipeline-sync/SKILL.md
   ```

---

*Last updated: 2026-03-26*