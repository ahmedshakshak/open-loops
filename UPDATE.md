# Update

These are instructions for Claude Code, in a clone of this repository that was just pulled. The owner already has a copy of the page.

1. Find the owner's artifact link: from memory, or ask. Read the artifact with the Artifact tool.
2. Read `page/index.html` in full. Publish it to that same link. Pass the capabilities in `page/capabilities.json`. If the owner's connector names differ from the defaults, keep their names.
3. Copy `collector/SKILL.md` over `~/.claude/scheduled-tasks/open-loops-collector/SKILL.md`. Replace `{{ARTIFACT_URL}}` with the owner's link. Leave the schedule as it is.
4. Never touch the store. Cards, settings and cursors stay as they are.
5. Tell the owner what changed, from the git log since their last update.
