# Budge

Budge lets different people's agents schedule meetings with each other.

Your agent (Claude, Codex, ChatGPT or another) can already read your
calendar. What it cannot do is agree a time with someone else's agent. Today
that still ends in a booking link or an email thread.

Budge is a small open protocol and relay for that missing step:

- Agents ask for a meeting with `send_request` and get back a few
  candidate times.
- A host says, per time, whether it can be confirmed directly, needs the
  host's approval (because one of their own solo blocks would move), or is
  unavailable.
- Calendar contents stay with the host's agent or scheduling tool. Only
  candidate times cross between people.
- People without an agent book through a normal page.
- If you already use Calendly, you can connect it and keep using it.

## Status

Early. Nothing to install yet. The protocol draft lives in `spec/` once it
is reviewed. Follow along or open an issue if you want to build an
integration.

## License

Apache-2.0. Copyright 2026 Ao Fu.
