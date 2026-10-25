# Budge

Tell it who and roughly when. Budge gets everyone to a time.

Budge is an open-source scheduling assistant for small meetings between
people who don't share a calendar system. You name 3 to 8 people and a
rough window. Budge then:

- emails each person and asks when they're free;
- reads their replies in plain words and checks back what it understood;
- sends at most two polite reminders;
- comes back to you only when there's a real choice to make;
- books the meeting on your calendar once you approve.

Invitees don't need an account, an app or a calendar connection. They
reply to the email or tap times on a private page.

## How it behaves

- **The AI only reads.** A language model turns each reply into
  constraints, one person at a time, and every reading is confirmed with
  the sender. It never picks a time, never writes the emails and never
  sees anyone else's answers.
- **A plain solver ranks the times, and you approve the booking.**
- **Every email says it comes from an AI scheduling assistant.** Each one
  names you as the organiser, says why it was sent, and offers a one-click
  way to stop all Budge email.
- **Nobody sees anyone's calendar.** Invitees see how many people can make
  a time, never who.

## Status

Design stage. Nothing to install yet. The v1 spec is in
[`spec/v1.md`](spec/v1.md), with the email templates in
[`spec/templates.md`](spec/templates.md) and acceptance tests in
[`spec/tests.md`](spec/tests.md). Feedback is welcome as issues.

v1 is deliberately small: Google Calendar organisers, English, one-off
meetings, and the organiser approves every booking. Microsoft, other
languages, recurring meetings and an agent-facing API come later, if v1
proves useful.

## License

Apache-2.0. Copyright 2026 Ao Fu.
