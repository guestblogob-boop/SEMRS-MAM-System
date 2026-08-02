# Client Message Log — Convention

This folder holds the real record of every message actually sent to a
client by the Client Communication Agent (see
agents/client-communication-agent.md and CLAUDE.md, Client
Communication). It's empty until a real order runs through the system
— nothing here is fabricated ahead of time.

## Structure
One subfolder per client order, per CLAUDE.md's Security & Misuse
Guardrails — "Multi-client separation":

```
outputs/client-message-log/
  <client-order-id>/
    message-log.md
```

`<client-order-id>` should be a stable, unique identifier for the
order (e.g. client business name + order date), matching whatever ID
the order uses elsewhere (client brief, approval records).

## Entry format
Each `message-log.md` is append-only (see Security & Misuse Guardrails
— "Append-only approval and message records"): never edit or delete a
past entry, only add new ones. Each entry should record, at minimum:

- **Timestamp**
- **Stage** (order received / awaiting order approval / order approved
  / awaiting final approval / delivered / declined / changes requested
  / client-initiated inquiry reply)
- **Channel** the message was sent on
- **Message sent** — the actual text, using the matching template from
  prompts/client-messages.md
