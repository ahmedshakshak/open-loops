# Open Loops

One page that lists everything waiting on you. It runs as a private Claude artifact that only you can open.

| Source | What shows up | How it closes |
| --- | --- | --- |
| Slack | Direct mentions, DMs, mentions of groups you pick | You tick it |
| Linear | Issues assigned to you, comments that mention you | Closes itself; you tick mentions |
| Calendar | Today's meetings, with "needs reply" and "declined" marks | Closes when the meeting ends |
| GitHub | Review requests, your open PRs with CI and review state, mentions | Closes on merge, close, or review given |
| Claude sessions | Your open Claude Code sessions, with a one-line status | You tick it |

Every card also has a Claude button. It sends the card, with an optional note, to a new or an existing Claude Code session.

## What you need

- The Claude desktop app, with the Code tab.
- The Slack, Linear and Google Calendar connectors turned on in claude.ai. A source you do not connect shows an error line and nothing else breaks.
- The GitHub command line (`gh`), signed in.

## Install

1. Clone this repository.
2. Open the folder in the Code tab of the Claude desktop app.
3. Say: `Follow SETUP.md`.

Claude publishes your own copy of the page, finds your accounts, and creates the scheduled task that feeds GitHub and Claude sessions. It asks you for your working hours and nothing else.

## Update

Pull this repository, open it in the Code tab, and say: `Follow UPDATE.md`.

## How it works

- `page/index.html` is the page. Slack, Linear and Calendar are read by the page itself, through your own connectors, every five minutes while it is open.
- `collector/SKILL.md` is a scheduled task for the Claude desktop app. It reads GitHub and your Claude sessions and writes them to the page's store. The desktop app must be running for it to fire.
- `docs/DISPATCH.md` tells the Claude session that published the page how to handle the Claude button and the Scan button.
- `docs/CONFIG.md` lists the settings. They live in your page's store, never in a file.

## Privacy

Each person installs their own copy. Your cards, settings and cursors stay in your own artifact's store. The page calls your connectors with your own sign-in. Nothing is sent anywhere else.
