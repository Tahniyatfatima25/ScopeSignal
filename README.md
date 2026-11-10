# ScopeSignal

Sort client feedback against a project brief. Keep the scope.

ScopeSignal is an independent portfolio concept for agency and freelance work. You paste a project brief and a client message. It splits the message into separate requests, checks each one against the brief, and sends them to you as notifications. Nothing moves forward until a person approves it.

**Live demo:** add your link here

> This is a prototype of the interaction. The sorting uses simple keyword rules, not an AI model. All examples are synthetic.

## The problem

Client messages mix bugs, preferences, new requirements and vague requests in one paragraph. Someone has to turn that into clear next steps without losing the original meaning or quietly accepting extra scope.

This is a hypothesis to test, not a claim about any specific company.

## How it works

1. **Brief.** Paste what you agreed to build.
2. **Message.** Paste what the client just asked for.
3. **Sorting.** Each request is checked against the brief and labelled.
4. **Your call.** Rate impact and effort, then accept, edit the next step, reject, or ask the client.
5. **Handoff.** Accepted items become a change log. Questions become a draft message.

Every request shows what the client asked for, the likely need underneath it, and the brief passage it was matched to, so you can check why it was sorted that way.

## Impact and priority

A request outside the brief is not automatically scope creep. Some feedback points to a real user need. For each request you set three things:

- **Impact:** low, medium or high
- **Effort:** low, medium or high
- **Real user need?** yes with evidence, no evidence, or unsure

From these the page works out a verdict and a priority.

| Verdict | When |
| --- | --- |
| In scope | Matches the brief |
| Fix | Looks like a bug |
| Worth exploring | Vague feedback that may hide a need |
| Scope change | Outside the brief, no evidence of a user need |
| Valuable discovery | Outside the brief, with evidence of a user need |

Priority comes from impact and effort: Do first, Do soon, Plan it, Backlog, or Skip for now. The change log is sorted by priority.

The "likely need" line is a guess from keywords. Treat it as a question to check with the client, not a fact.

## Request labels

| Label | Meaning |
| --- | --- |
| Inside the brief | Matches something already agreed |
| New scope | Asks for something the brief does not cover or limits |
| Outside the brief | The brief says it is out of scope |
| Unclear request | Vague wording such as "simpler" or "nicer" |
| Possible bug | Describes something broken |

## What is in the page

- Landing page with a frosted card over a WebGL plasma background
- Three step demo: paste, review, export
- Requests arrive one at a time as notifications, with filters
- Each request shows what was asked and the likely need underneath
- Impact, effort and user need ratings, with a verdict and priority
- Editable next steps, a change log sorted by priority, and a draft client message, with copy to clipboard
- Footer with the wordmark and an orb whose eyes follow the pointer

## Tech

- One HTML file, no build step, no framework
- Plain JavaScript and CSS
- WebGL1 for the background and the orb, no libraries
- Fonts from Google Fonts: Instrument Serif and DM Sans
- Respects reduced motion, pauses animation when the tab is hidden, caps pixel ratio at 2

## Run it locally

1. Save the page as `index.html`.
2. Open it in a browser, or serve the folder:

```bash
npx serve .
```

WebGL and the Google Fonts request need a normal browser with internet access. If WebGL is unavailable, the page falls back to a plain dark background.

## Project structure

```
index.html    page, styles, shaders and demo logic
README.md
```

## Limits

- The classifier is rule based. It matches shared words between a request and a brief line, so it will miss paraphrases and can misread conflicting requests.
- Splitting works on commas, "and" and sentence ends, so long compound requests can split badly.
- Nothing is saved. Refreshing clears the demo.

## Next steps

- Replace the rules with an LLM call behind a small server function, returning JSON with the request, label, quote from the message, quote from the brief and a confidence note
- Check that each returned quote really appears in the input
- Run a small test with 3 to 5 designers or project managers and record time to a usable action list, missed or wrong labels, and corrections before approval
- Write up one failure and the fix

## Credits

- Plasma background shader settings exported from the 21st.dev Shader Builder
- Orb character based on the LiveOrb component, ported to plain JavaScript
- Fonts: Instrument Serif and DM Sans, via Google Fonts

## Disclaimer

ScopeSignal is not made or endorsed by any company. Do not paste real client conversations without permission.

## License

Add your license here.
