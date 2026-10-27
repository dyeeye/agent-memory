# agent-memory

Long-term memory of Max's account agent. The agent reads and writes these files through the GitHub MCP server. Every write is a commit, so you can see what the agent saved, when, and why. If it saved something wrong, revert the commit.

Keep this repository **private**. Give the agent a fine-grained token with access to this repository only (Contents: read and write).

## One file per client

Every client has one Markdown file in `clients/`. The file name comes from the company name, with this rule:

1. Write the name in lowercase.
2. Remove the legal form: AB, GmbH, Ltd, Oy, Inc, LLC, S.A., and similar.
3. Keep only letters, digits and spaces. Remove `&`, dots and commas.
4. Join the words with `-`.

| Company name | File |
|---|---|
| Kestrel Pumps GmbH | `clients/kestrel-pumps.md` |
| Kestrel Pumps | `clients/kestrel-pumps.md` |
| Alder & Finch Oy | `clients/alder-finch.md` |

So the same client always gets the same file, also when somebody writes the name a little differently.

## What goes into the file

Only agreements: facts that stay true for a while, decisions, and promises with a date. For example, the contact person, delivery dates, payment terms, prices, and open promises. No small talk, and never the whole conversation.

Use one row per topic. A new agreement on the same topic **replaces** the old row. It doesn't add a second one.

```markdown
# Kestrel Pumps GmbH

| Topic | Agreement | Source | Saved |
|---|---|---|---|
| contact | Jonas Weber, senior buyer | call with the sales rep | 2026-10-27 |
| first-delivery | 2027-03-02, then every Tuesday | call with the sales rep | 2026-10-27 |
| payment | 30 days from the invoice date | call with the sales rep | 2026-10-27 |
```

- **Topic**: a short key, for example `contact`, `first-delivery`, `payment`, `price`, `other`.
- **Agreement**: the exact values: names, dates as `YYYY-MM-DD`, numbers.
- **Source**: where the agreement came from.
- **Saved**: the date of the write.
