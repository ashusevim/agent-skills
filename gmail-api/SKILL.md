---
name: gmail-api
version: 1
source: https://developers.google.com/workspace/gmail/api/guides
description: Send, read, and search Gmail via the API. Use when sending mail with messages.send, managing drafts, listing and filtering messages with search queries, handling threads and labels, or choosing OAuth scopes.
---

# Gmail API

Drive a mailbox programmatically: OAuth with minimal scopes, send MIME as base64url, search with Gmail query syntax.

Sources: API overview, sending guide, filtering guide. Endpoint patterns in `references/flows.md`.

## When to use

- Sending mail (`messages.send`) or staging drafts first
- Listing/searching messages (`messages.list` + `q`), threads, labels
- Replies that stay threaded; attachments; error handling
- Picking OAuth scopes for a Gmail integration

## Instructions

1. **Scope to the job.** Sending only → `gmail.send`; drafts → `gmail.compose`; read+labels → `gmail.readonly` or `gmail.labels`; full mailbox → `gmail.modify` (never full `gmail` scope unless settings change). Done when: no scope exceeds the task.
2. **Send as base64url MIME.** Build RFC 2822 MIME (To/From/Subject/body) → `base64.urlsafe_b64encode` → `{"raw": …}` → `POST users/me/messages/send`. Drafts: same body under `{"message": {"raw": …}}` to `users/me/drafts`, then `drafts.send`. Done when: send returns a message id.
3. **Thread replies deliberately.** Match `Subject`, set `References` + `In-Reply-To` per RFC 2822, or the reply starts a new thread. Done when: reply appears in the same thread.
4. **Search with `q`, filter with labels.** `GET users/me/messages?q=…` supports Gmail syntax (`in:sent after:2014/01/01`, `from:`, `has:attachment`); dates are PST midnight — use epoch seconds for other zones. Add `labelIds[]` for label scoping. API ≠ UI: no alias expansion, no thread-wide search. Done when: query returns the intended set, verified against one known message.
5. **Handle the error, not the retry.** 403 = scope/auth problem (fix creds, don't resend); 429/5xx = back off. Done when: each error class maps to one action.

## References

- `references/flows.md` — send/draft/search recipes (Python + cURL)

## Changelog

- v1: initial build from Gmail API guides (overview + sending + filtering)
