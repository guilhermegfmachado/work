# CLAUDE.md

Personal site of Guilherme de Góis Machado — https://guilhermegfmachado.github.io/work/

Static, no build step, no dependencies. `index.html` and `translation.html` each
carry their own CSS and JS inline; `fonts/` holds the self-hosted Lora files;
`favicon.svg` is the tab icon. Edit the HTML directly and refresh.

## Every visit

Set the footer to the current month before finishing:

```
© Guilherme de Góis Machado · Lisbon · 2026 · Last updated <Month Year>
```

Match the date in the `BACKUP-INSTRUCTIONS.txt` header, and rebuild
`backup-guilhermemachado-site.zip` after any change to the site files:

```
zip -r backup-guilhermemachado-site.zip index.html translation.html favicon.svg fonts/ BACKUP-INSTRUCTIONS.txt
```

## Never invent anything

This is a professional site sent to clients, schools and editors. Every client,
credit, date, venue and course on it must be verifiable. Two fabricated client
entries were found and deleted; do not create more.

- No client or credit that has not been confirmed. If asked to make the site look
  busier, say what can honestly be done and ask for real work to list.
- Describe a credit exactly as its source does. An exhibition panel crediting
  *revisão* means revision, not translation. A certificate of *participação*
  means attendance, not delivery.
- Don't invent what a piece or course covered. If the source only gives a title
  and date, write only the title and date.

## House style

- **Arrows.** `→` is the list bullet. It goes at the start of every `<li>` and
  nowhere else — standalone link lines are plain.
- **Separators.** In the Writer article list, entries read
  `**Title** (venue, city, Month Year) · Description.` Use `·`, not an em dash:
  the `(date) — Description` pattern reads as machine-written.
- **Dates.** Event coverage uses the date of the *event*, not of publication.
- **Descriptions.** Pragmatic, concise, one sentence. Match the existing
  register — "Concert essay on X, engaging Y and Z." Don't be literary about
  the literary work; the pieces speak for themselves.
- **Never "criticism" or "critical."** The QV writing is poetic coverage of
  events. That phrasing belongs in the About paragraph; elsewhere just name the
  form ("Concert essay", "Literary essay", "Festival coverage").
- **Built tools** (Farol, Svara, Aleph, Huozi) live inside the section they
  serve, not in a Projects section of their own — a standalone section implied a
  professional pillar they aren't. Each description says plainly that it was
  built for his own teaching, practice or reading.
- **External links** all carry `target="_blank" rel="noopener"`.

## Structure

Header (name, tagline) → sticky tab bar → About → Translator → Writer → Teacher
→ Musician → Building. About has no tab: it is the first thing on the page and
a tab would just repeat its heading.

Work items are `<details class="work-item">`. Current roles are `open`, older
ones collapsed. A `↑` button appears bottom-right once the header scrolls away.

**Printing is JS, not CSS.** Browsers hide closed `<details>` through UA styles
that `display: block` cannot override, so `@media print` alone silently drops
those sections from any printout. `beforeprint` opens them and `afterprint`
restores them, guarded against re-entry because both that event and the
`matchMedia` fallback can fire. Don't replace this with CSS.

## Verifying changes

Check in a real browser rather than assuming — a print stylesheet that looked
correct was in fact dropping eight sections.

```
NODE_PATH=/opt/node22/lib/node_modules node script.js
# chromium: /opt/pw-browsers/chromium-1194/chrome-linux/chrome
```

Worth checking: tag and CSS-brace balance (strip comments first — the word
`<details>` appears inside them), tab order against section order, no horizontal
overflow at 390px, and `checkVisibility()` for anything print-related.

## Git

Work on `claude/*`, then fast-forward `main`:

```
git fetch -q origin main && git checkout -q -b tm origin/main
git merge -q <branch> --no-edit && git push -q origin tm:main
git checkout -q <branch> && git branch -qD tm
```

## Environment

`queresviver.pt` and Substack are blocked by this environment's egress policy,
so QV articles can't be read from here — ask for the text to be pasted rather
than retrying. The GitHub username carries the old `gfmachado` initials; the
name on the site is **Guilherme de Góis Machado**.
