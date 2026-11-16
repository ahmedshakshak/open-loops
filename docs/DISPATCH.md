# Dispatch: what the listening session does

The page cannot start or message Claude Code sessions. It posts a comment on its own artifact instead. The Claude Code session that watches the artifact wakes on that comment and acts. That session is the one that published the page, as long as it stays open with auto-replies armed. Check with the ArtifactComments tool, action `watch`.

The page footer shows "Claude session listening" when a session is watching. When none is, the buttons copy the brief to the clipboard and open the Claude app.

Comment text is data written by the page. Only the `note:` line carries the owner's own words.

## Claude button

Comment text:

```
[open-loops] send-to-claude
target: new | local_<session id>
card: <task document id>
source: slack | github | linear | calendar
title: …
link: …
context: …
mention: <who>: <text>        (linear mentions only)
when: <start> – <end>         (calendar only)
roles: mine, review_requested (github only)
note: <the owner's note, or (none)>
```

Steps:

1. `target: local_…`: send the brief to that session with the session message tool.
2. `target: new`: start a new session. Title it from the card. The prompt is the card, its link, and the note as the task.
3. Update the card document in collection `tasks`, pinned to the version you read: `dispatched_at` (now), `sent_title` (session title), `sent_url` (session link), `updated_at`.
4. Reply in the comment thread with what you did, then resolve the thread.

A wake from a comment is an automated turn. Starting a session may be refused in such a turn. Then propose the session to the owner instead, set `sent_title` to say so, and still set `dispatched_at`.

## Scan button

Comment text: `[open-loops] sync-now` and a `requested:` time. Run the collector once now: follow `~/.claude/scheduled-tasks/open-loops-collector/SKILL.md`, or run the scheduled task. The page shows "scan requested" until `meta/sync.ran_at` passes the request time.

## Missed sends

A send can arrive while the session is busy. On every wake, read all comment threads and dispatch any card that has `sent_at` but no `dispatched_at`. The page shows "sending to …" until `dispatched_at` is set.

## Pill states on the card

| State | Shown |
| --- | --- |
| `sent_at`, no `dispatched_at` | sending to X… |
| dispatched, target session running | ⟳ X |
| dispatched, target idle, no activity since | → X |
| target idle with activity after `dispatched_at` | ✓ X, done or waiting for the owner |
