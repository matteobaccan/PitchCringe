# Struttura canonica e regole Marp

## Lo scheletro (non si tocca)

La forza del cringe da pitch è la forma perfetta (vedi `tassonomia.md`). Il deck segue
sempre questo ordine. Le slide fra parentesi sono opzionali e si aggiungono in base ai
moduli scelti.

| # | Slide | Modulo tipico |
|---|-------|---------------|
| 1 | Copertina: nome, tagline, "Seed round · [mese anno]" | P03, P04, P27 |
| 2 | Problema | P01, P02 |
| 3 | Soluzione | P03, P04, P13 |
| 4 | Prodotto / Demo | P14, P15 |
| (4b) | Why now | P05 |
| 5 | Mercato (TAM/SAM/SOM) | P06 |
| 6 | Business model | P18, P34 |
| 7 | Traction | P07, P08, P09, P12, P35 |
| 8 | Competizione | P11, P17 |
| 9 | Go-to-market | P24 (spesso confuso con use of funds) |
| 10 | Team | P19, P20, P21 |
| 11 | Proiezioni finanziarie | P10, P34 |
| 12 | Ask e use of funds | P23, P24, P26 |
| (12b) | Exit | P25 |
| 13 | Vision / Grazie | P04, P27, P28 |
| (13b) | Appendice | P33 |
| 14 | **Disclaimer** (sempre, vedi SKILL.md) | |

Lunghezza per registro: credibile 10-14 slide; parodico può arrivare a 18; surreale
resta corto, 10-12, perché il contrasto regge meglio in poco spazio.

## Formato Marp

Il file è markdown standard con le direttive Marp. Regole di costruzione:

### Frontmatter e tema della casa

Base `uncover`, più lo stile della casa nel campo `style:` del frontmatter. Il
deck deve sembrare curato (il founder ha pagato qualcuno per il template): titoli
Space Grotesk con sottolineatura sfumata, corpo Inter, lead su gradiente
blu-viola, sfondi con glow radiali tenui. Aggiungi `footer:` solo con P36.

```markdown
---
marp: true
theme: uncover
paginate: true
style: |
  @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;700&family=Inter:wght@400;600&display=swap');
  section {
    font-family: 'Inter', 'Segoe UI', sans-serif;
    background:
      radial-gradient(620px 320px at 92% -8%, rgba(91, 108, 250, 0.09), transparent 60%),
      radial-gradient(520px 300px at -8% 108%, rgba(160, 93, 246, 0.08), transparent 60%),
      #fbfaf6;
    color: #1d2433;
    font-size: 26px;
    padding: 64px 76px;
    justify-content: flex-start;
    text-align: left;
    letter-spacing: normal;
  }
  section p, section li, section td, section th { letter-spacing: normal; }
  section h2 {
    font-family: 'Space Grotesk', 'Segoe UI', sans-serif;
    font-size: 1.45em;
    letter-spacing: -0.02em;
    text-align: left;
    margin-bottom: 0.5em;
  }
  section h2::after {
    content: '';
    display: block;
    width: 70px;
    height: 5px;
    margin-top: 12px;
    border-radius: 3px;
    background: linear-gradient(90deg, #5b6cfa, #a05df6);
  }
  section strong { color: #5b6cfa; }
  section em { color: #7a8194; }
  section table { margin: 0.4em 0; }
  section th { background: #eef0ff; color: #3d4bd6; padding: 0.45em 0.9em; }
  section td { padding: 0.45em 0.9em; }
  section ul { margin-left: 0; }
  section li { margin-bottom: 0.25em; }
  section.lead {
    background:
      radial-gradient(720px 420px at 14% 18%, rgba(255, 255, 255, 0.16), transparent 60%),
      linear-gradient(135deg, #4653f0 0%, #7b52f4 55%, #a95cf0 100%);
    color: #ffffff;
    justify-content: center;
    text-align: center;
  }
  section.lead h1 {
    font-family: 'Space Grotesk', 'Segoe UI', sans-serif;
    font-size: 2.7em;
    letter-spacing: -0.03em;
  }
  section.lead h3 { font-weight: 500; color: rgba(255, 255, 255, 0.88); }
  section.lead strong { color: #ffe27a; }
  section.lead em { color: rgba(255, 255, 255, 0.75); }
  section.lead a { color: #ffe27a; }
  section.lead::after { color: rgba(255, 255, 255, 0.6); }
---
```

### Separatore di slide

Tre trattini su una riga vuota: `---`. **Mai** usare `---` dentro il contenuto di una
slide (nemmeno come linea orizzontale): Marp lo legge come nuova slide.

### Classe lead

Copertina, slide con una sola frase (P04, P27, P30 "SCALABILE.") e slide "Grazie"
usano la classe lead, che centra tutto:

```markdown
<!-- _class: lead -->
# Titolo enorme
### sottotitolo
```

Il trattino basso davanti a `_class` la applica alla singola slide.

### Note del presentatore (P31)

Marp tratta i commenti HTML come note del relatore, tranne quelli che contengono
direttive (`_class`, `_backgroundColor`, ecc.). Le note vanno in fondo alla slide:

```markdown
## La nostra traction

- 2.400 utenti registrati
- +312% MoM

<!-- Pausa. Lasciare che il numero faccia effetto. Se chiedono gli attivi, andare avanti. -->
```

Una nota per slide al massimo. Le note sono in italiano e in seconda persona
(il founder che scrive a se stesso).

### Immagini

**Non inserire immagini reali né link a immagini.** Dove il deck vero avrebbe una
foto, un grafico o una griglia di loghi, metti una descrizione fra parentesi quadre,
in corsivo, e falla lavorare per il cringe:

```markdown
*[grafico a linee, sale verso destra, asse Y senza unità]*
*[foto del team: tre persone, una è tagliata]*
*[griglia di 12 loghi, 9 sono aziende in cui abbiamo fatto lo stage]*
```

Il modo in cui è descritta l'immagine assente è uno dei punti più forti del formato:
è la voce dell'investitore muto che si insinua (vedi tassonomia).

Se l'utente vuole poi generare le immagini, in coda al deck la skill propone i prompt
(vedi SKILL.md, sezione Consegna).

### Tabelle

Le proiezioni (P10) e i confronti coi competitor (P11) vanno in tabelle markdown.
Marp le rende bene. **Tetto: 4 colonne di dati più la colonna delle etichette** (5 in
tutto) e 5 righe più l'intestazione. A 5 colonne di dati la slide è al limite, con
intestazioni lunghe trabocca.

### Dimensione del testo

Una slide Marp contiene comodamente: un titolo, una riga di apertura, 4-5 bullet
sotto i 90 caratteri (uno può andare a capo, non due), una riga di chiusura. Oppure
una tabella (limiti sopra) e una riga sotto. Oppure una frase sola in lead. Un
placeholder immagine di due righe conta come un bullet. Il feature-dump (P14) va oltre di proposito: 12-15 bullet in
una slide, e la nota dice "font ridotto per farci stare tutto".

### Cosa non fare

- Niente HTML inline oltre i commenti e le direttive: il deck deve aprirsi con
  qualunque Marp, incluso il plugin VS Code.
- Il CSS sta tutto nel blocco `style:` della casa (sopra): non aggiungerne altro
  ad hoc e non deformare lo scheletro per fare scena.
- Niente `![bg]` con URL esterni.
- Niente `---` interni alle slide.
- I deck con immagini locali si renderizzano con `--allow-local-files`
  (`npx @marp-team/marp-cli deck.md --allow-local-files -o deck.pdf`).

## Prompt per le immagini (opzionale, in consegna)

Se l'utente vuole le immagini, per ogni placeholder proponi un prompt. **Le immagini
devono sempre sembrare reali**: fotografie con luce naturale e grana da telefono,
mai render patinati o estetica da illustrazione. Il cringe sta nel soggetto, non
nella fattura. Ogni immagine va poi in una slide dedicata con un titolo da manifesto
(vedi SKILL.md, regole fisse).

- In inglese, con una riga in italiano che dice cosa raffigura; chiedi sempre
  "photorealistic, natural lighting, looks like a real photo".
- I grafici non si generano come foto: il grafico delle proiezioni è un SVG
  costruito sui dati e sta nella stessa slide della tabella (vedi SKILL.md,
  regole fisse).
- Per il team: mai persone riconoscibili, "two people from behind, jumping in an
  empty parking lot, one partially cropped, phone photo".
- Niente testo leggibile in scena (i loghi e i nomi si descrivono, non si mostrano).
- Aspect ratio 16:9.
