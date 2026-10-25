# Email templates (v1 draft)

Every email Budge sends. Outbound text is only these templates with fields
filled from the database; the language model never writes outbound text.
`{…}` marks a field. `[Button]` marks a link to a signed page action.
Opening a link only shows a page; a button press on the page changes
state.

Times are always shown in the recipient's zone with date, local time and
zone, for example "Wed 29 Oct, 14:00 to 14:45 (London, UTC+0)". If the
recipient's zone is a guess, the line ends with
"(your time zone is a guess: [correct it])".

## Invitee footer (on T1 to T5)

```
Why you got this: {organiser.name} ({organiser.email}) added your address
to this meeting and asked Budge to find a time. Budge emails you only about
this meeting, at most three times, plus confirmations of your own answers.
Stop all emails from Budge: {unsubscribeUrl} · Privacy notice: {privacyUrl}
Budge, {operator.legalName}, {operator.postalAddress}
```

## T1 · First invitation (organiser in cc)

Subject: `{organiser.name} is finding a time for "{meeting.title}"`

```
Hi {invitee.firstName},

I'm Budge, an AI scheduling assistant. {organiser.name} asked me to find a
time for "{meeting.title}" ({meeting.durationText}, {meeting.modeText})
with {otherInviteesText}, between {window.startText} and {window.endText}.

Which times work for you? Two ways to answer:
- Reply to this email in your own words, for example "not Tuesdays,
  afternoons are best". I'll confirm what I understood before it counts.
- Or pick times on this page: {pageUrl}

If you'd rather not take part, you can say so on the same page.
{organiser.firstName} will see that you stepped out, nothing more.

Thanks,
Budge, for {organiser.name}
```

`{otherInviteesText}` lists first names, for example "Ben, Chen and Dee".
Above 4 names it becomes "Ben, Chen and 3 others".

## T2 · Echo confirmation (after a free-text reply)

Subject: `Re: {T1 subject}`

```
Hi {invitee.firstName}, here's what I understood from your reply:

{constraintSentences}

Is that right? [Yes, that's right] [Fix it]

Until you confirm, {organiser.firstName} sees your answer as unconfirmed.
```

`{constraintSentences}` is built in code from the parsed constraints, one
line each, for example "- Not on Tuesdays" or "- Afternoons (12:00 to
18:00, London) preferred".

**Variant, nothing usable found:**
```
Hi {invitee.firstName}, I couldn't read any times from your reply. Could
you pick them here instead? {pageUrl}
```

**Variant, out-of-office detected:**
```
It looks like you're away until {date}. Should I treat you as unavailable
until then? [Yes] [No]
```

## T3 · Reminder 1 (2 working days after T1, no answer)

Subject: `Re: {T1 subject}`

```
Hi {invitee.firstName}, a quick follow-up from Budge,
{organiser.name}'s AI scheduling assistant. Any times that don't work for
you between {window.startText} and {window.endText}? A short reply like
"anything except Monday" is enough. Or: {pageUrl}
```

## T4 · Reminder 2 (2 working days after T3): three offers, last reminder

Subject: `Re: {T1 subject}`

```
Hi {invitee.firstName}, would any of these work for "{meeting.title}"?

- {offer1Text}  [Works]
- {offer2Text}  [Works]
- {offer3Text}  [Works]
- [None of these]

This is my last reminder. After this, {organiser.firstName} will decide
how to go ahead.
```

The three times are `offer` claims (spec §6).

## T5 · Withdrawal (a picked time was taken)

Subject: `Re: {T1 subject}`

```
Hi {invitee.firstName}, sorry: {withdrawnText} has just been taken. These
times still work for the group so far:

- {optionText}  [Works]   (one line per remaining option, at most 3)
- [None of these]
```

## Organiser emails (organiser only, no invitee footer)

| Id | When | Subject | Body |
|---|---|---|---|
| O1 | Sign-in | `Your Budge sign-in link` | The magic link; it expires in 15 minutes |
| O2 | A new decision is needed | `"{meeting.title}": {decisionHeadline}` | The decision in one line, up to 3 options as buttons, and a link to the status page |
| O3 | Booked | `"{meeting.title}" is booked for {slotText}` | The final time, who's coming, and a reminder that the invite came from their own calendar |
| O4 | Trouble | `"{meeting.title}" needs you: {problem}` | Google access lost, a calendar conflict found, sending paused, or the operator took over; then what happens next |

Decision headlines for O2:
- "pick a time"
- "nobody fits, choose a fallback"
- "{name} hasn't answered"
- "{name} stepped out"
- "{name} sent a Calendly link"
- "{name} answered for someone else"
- "{name} declined the booked time"
