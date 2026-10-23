# Budge

Let other people's AI book you.

Connect your Calendly once and you get a link like `usebudge.dev/you`.
Anyone can then tell their own assistant, Claude, ChatGPT or another,
"book 30 minutes with usebudge.dev/you next week", and the meeting is
booked. No booking page to open, no email back-and-forth.

Why this needs a small open layer: booking someone's Calendly through its
API requires that person's permission, so an assistant cannot do it on its
own. Budge is that one-time permission, plus two tools any assistant can
call: `find_times` and `book`. Calendly still sends the invites.

## Status

Early. Nothing to install yet. The protocol draft will live in `spec/`
once it is reviewed. Open an issue if you want to build an integration.

## License

Apache-2.0. Copyright 2026 Ao Fu.
