# Setup

These are instructions for Claude Code, running in the Claude desktop app, in a clone of this repository. The person who asked you to follow this file is the owner of the new copy.

Rules for the whole setup:

- Publish a new artifact. Never publish over an existing one.
- Ask the owner only what this file tells you to ask.
- The kit needs no passwords, tokens or keys. Do not ask for any.
- Write nothing personal into the files of this repository. Settings go in the artifact's store.

## 1. Check what is there

- Run `gh auth status`. If `gh` is missing or signed out, tell the owner. The GitHub column stays empty until it is fixed. Continue.
- Check that the scheduled-task tools and the session tools of the desktop app are available. If they are not, the owner is not in the desktop app. Tell them the GitHub and Claude sessions columns need it. Continue with the page only.

## 2. Publish the page

1. Read `page/index.html` in full.
2. Publish it with the Artifact tool as a new artifact. Use the capabilities in `page/capabilities.json` exactly. Icon: `checklist`.
3. The connector names in the capabilities must match the owner's connector names in claude.ai: `Slack`, `Linear`, `Google Calendar`. If a publish warning or the owner says a name differs, change that name in the capabilities you pass and in the `callTool` calls of your published copy. Do not edit the repository file.
4. Keep the artifact link. The rest of this file calls it ARTIFACT_URL.

## 3. Write the settings

Create the document `meta/config` with the ArtifactData tool. Fields are in `docs/CONFIG.md`.

- `slack_user_id`: read it with the Slack profile tool if you have one. Otherwise leave it out. The page finds it on its first pull.
- `slack_team_id`: leave it out unless the owner gives it.
- `github_owners`: ask the owner once: "Track GitHub items from every repository, or only from some organizations?" Store the organization names, or an empty array.
- `slack_seed_words`: an empty array.

## 4. Install the collector

1. Copy `collector/SKILL.md` to `~/.claude/scheduled-tasks/open-loops-collector/SKILL.md`. Replace `{{ARTIFACT_URL}}` with ARTIFACT_URL.
2. Ask the owner for their working days and hours.
3. Create a scheduled task named `open-loops-collector` that runs that file every 30 minutes inside those hours.
4. Run the collector once now, by following the installed file yourself. Report its summary line. The first run asks the owner to allow `gh`, the artifact store and the session tools. Tell them to choose "always allow" so later runs are silent.

## 5. Become the listener

1. Read `docs/DISPATCH.md`.
2. Confirm with the ArtifactComments tool, action `watch`, that this session watches ARTIFACT_URL with auto-replies armed.
3. Save a memory for future sessions: the artifact link, the collector path, and the dispatch duty from `docs/DISPATCH.md`.
4. Tell the owner: this session receives the Claude button and the Scan button while it stays open. A later session can take over with the `watch` action on the same link.

## 6. Hand over

Tell the owner, in a few lines:

- The link to their page.
- On first open, the page asks to use Slack, Linear and Calendar. Allow them.
- The Groups button adds Slack groups whose mentions count as theirs.
- The Float button opens a small always-on-top window.
- What is not working, if anything, and why.
