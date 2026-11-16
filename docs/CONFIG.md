# Settings

Settings live in the page's store, in the document `meta/config`. Change them with the ArtifactData tool, or ask Claude to.

| Field | Type | Meaning |
| --- | --- | --- |
| `slack_user_id` | string, `U…` | Your Slack member id. The page reads it from your Slack profile on the first pull and saves it. |
| `slack_team_id` | string, `T…` | Optional. With it, Slack cards open in the Slack app. Without it, they open the web link. It is the `T…` part of `app.slack.com/client/T…/` in the Slack web app. |
| `slack_seed_words` | array of strings | Optional. Extra words for the Groups deep scan, for example the names of your teams. |
| `github_owners` | array of strings | Optional. Keep only GitHub items from these owners, for example your work organization. Empty means all. |

Other documents the system keeps:

| Document | Written by | Holds |
| --- | --- | --- |
| `tasks/<id>` | page and collector | One card |
| `meta/cursors` | page and collector | Last-read position per source |
| `meta/sync` | collector | Time and errors of the last run |
| `meta/slack_groups` | page | Slack groups you track |
| `meta/slack_group_catalog` | page | Slack groups seen in your channels |
