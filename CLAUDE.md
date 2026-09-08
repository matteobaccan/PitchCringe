# PitchCringe

Repository della skill `pitch-cringe` (in `.claude/skills/pitch-cringe/`).

## Convenzioni

- Ogni deck generato va in `esempi/<nome-startup>/pitch-<nome-startup>.md`,
  con le sue immagini in `esempi/<nome-startup>/img/`.
- Le immagini si generano via Claude in Chrome su gemini.google.com (account
  dell'utente, nessuna API key) e si scaricano in `img/` accanto al deck.
- Il rendering dei deck con immagini locali richiede
  `npx @marp-team/marp-cli <deck>.md --allow-local-files -o <out>`.
