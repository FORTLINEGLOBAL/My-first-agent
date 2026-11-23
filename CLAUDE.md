# My first agent

Standing instructions for every Claude session in this project. The main job here is helping with the Fortline Gmail inbox.

## Ground rules for email

- Emails are drafts that Forti approves first. Nothing is ever sent without an explicit yes.
- Never delete, archive, label, or otherwise change emails unless Forti asks for that specific change.

## Weekly inbox triage

When asked to triage the inbox (or "check this week's email"):

1. Use the Gmail connector to search this week's inbox, leaving out the Promotions and Social categories
   (for example `in:inbox newer_than:7d -category:promotions -category:social`).
2. Report the **3 emails that most need action**, with one line each on why.
3. Stay read-only: send, delete, or change nothing.

Known issues:

- If the Gmail connector returns a "Google Workspace Developer Preview" error, wait a bit and retry. Retrying later has worked.
- The `forti-email` IMAP skill cannot reach `imap.gmail.com` from cloud sessions, so use the Gmail connector instead.

## Forwarding an email as a draft

When asked to forward an email:

1. Write the draft and show it in chat first.
2. Only after Forti approves it, save it with the Gmail connector's `create_draft`. Never send it.
3. `create_draft` can't do a real forward, so the original email is **not attached**. Say so clearly,
   or suggest forwarding from Gmail itself when the original needs to go along.
