---
name: pitch-cringe
license: MIT
description: "Genera pitch deck di startup cringe in formato Marp (markdown, una slide per sezione), in italiano di default ma in qualunque lingua, calibrati su livello di cringe (1-10), registro (credibile / parodico / surreale deadpan), fase (pre-seed, seed, Serie A), voce del founder e moduli cringe scelti da un catalogo di 36. Usala quando l'utente chiede un pitch deck, un pitch, un deck per investitori, una presentazione da startup, un elevator pitch parodia, il deck dell'Uber di X, un pitch cringe, finto, satirico o assurdo, oppure vuole parodiare il modo in cui le startup si presentano ai fondi. Companion di linkedin-cringe: stessa tassonomia, stessi paletti, formato diverso."
---

# Pitch Cringe: generatore di pitch deck

Genera pitch deck in formato Marp che riproducono il cringe autentico delle startup
italiane (e non solo) in cerca di soldi.

## Principio guida

Il cringe da pitch è **imbarazzo vicario davanti a un investitore muto**: il founder ci
crede, il deck rivendica un mercato, una tecnologia e una squadra che le slide non
reggono, e vuole soldi fingendo di fare un favore a chi li dà.

**Regola non negoziabile: la voce non strizza mai l'occhio.** Nessuna slide sa di essere
ridicola. Appena una slide ammicca, il deck smette di essere cringe e diventa una
barzelletta. L'unico posto dove la voce può ammiccare è la slide finale di disclaimer.

**Seconda regola: la forma è perfetta.** Copertina, problema, soluzione, mercato,
business model, traction, competizione, team, proiezioni, ask. Il founder ha letto le
guide. Il cringe sta nel contenuto delle caselle, mai nella loro assenza.

Leggi `references/tassonomia.md` prima di scrivere: contiene la definizione operativa,
la legge dello scarto nella versione pitch, la scala 1-10 e i registri.

## Flusso

### 1. Raccogli i parametri

Se l'utente ha già indicato settore, livello, fase o moduli nella richiesta, **non fare
domande**: usa quello che ha detto e riempi i buchi con i default (livello 7, credibile,
seed, voce ex consulente).

Altrimenti mostra prima il **menu dei moduli** (elenco compatto, codice + nome, preso da
`references/moduli.md`) e poi chiedi i parametri con **AskUserQuestion**, quattro
domande:

**D1. Livello di cringe** (`header: "Livello"`)
- `4` Lieve: un deck fastidioso ma a cui un investitore risponderebbe
- `7` Imbarazzante (consigliato): il punto dolce, il deck che gira fra gli analisti
- `9` Insostenibile: screenshottabile, finisce nel gruppo dei founder
- `10` Leggendario: tutti i tic insieme, appendice compresa

**D2. Registro** (`header: "Registro"`)
- `Credibile (consigliato)`: deve poter passare per un deck vero, arrivato a un fondo
  il martedì pomeriggio. Nessuna esagerazione che tradisca la finzione
- `Parodico`: la satira è dichiarata, le esagerazioni si vedono. Vive dall'8 in su
- `Surreale deadpan`: la startup vende qualcosa di impossibile e il deck non se ne
  accorge. Nessuna battuta. Vive dal 7 in su, punto dolce 9

**D3. Voce del founder** (`header: "Voce"`)
- `Ex consulente`: framework ovunque, TAM a tre cerchi, gergo VC quasi giusto
- `Tech-bro`: buzzword stack, moat immaginario, ha già deciso a chi vendere
- `Primo pitch`: sincero, entusiasta, origin story col nonno, sei C-level in due
- `Imprenditore tradizionale che si fa startup`: ha un'attività vera e vuole "farla
  diventare una piattaforma"

**D4. Moduli cringe da inserire** (`header: "Ingredienti"`, `multiSelect: true`)
Quattro combo pronte; l'utente può usare "Other" per scrivere i codici del catalogo
(es. `P06, P07, P23`):
- `La classica` (P06 + P07 + P23): mercato enorme, grafico che sale, valutazione assurda
- `Il primo pitch` (P01 + P02 + P08 + P20 + P28)
- `Il tech-bro` (P03 + P13 + P17 + P25)
- `Pacchetto completo`: scegli tu i moduli coerenti col livello

Se manca il **settore** (o l'idea della startup), chiedilo a parte in chat con una
riga, non con AskUserQuestion. Stessa cosa se l'idea è descritta in poche parole e
ammette più prodotti diversi ("pastiglie per profumare la cacca": si ingeriscono o si
buttano nel water?): una riga in chat prima di scrivere, mai un deck su un'ipotesi. Se l'utente dice "inventa tu", inventa un'idea piccola
e plausibile (un'app per una nicchia banale): il cringe cresce meglio su un'idea
modesta che su un'idea assurda, salvo in registro surreale.

**Fase** (pre-seed, seed, Serie A): si deduce dalla richiesta, default seed. Non è
una quinta domanda. Cambia le cifre dell'ask e quanto stona ogni modulo (le proiezioni
al 2030 in pre-seed sono più cringe che in Serie A).

**Registro surreale (opzionale).** Si attiva da solo quando l'utente scrive "surreale",
"assurdo ma serio", "alla David Lynch", oppure descrive un prodotto che non può
esistere: in quel caso dai il registro per scelto e porta il livello di default a 9.
Prima di scrivere leggi `references/surreale.md`: otto regole, repertorio di fisiche
impossibili, cosa cambia nei moduli.

**Gancio reale (opzionale).** L'utente può dare un dato di mercato vero, una notizia o
un trend reale ("prendi spunto dal dato X"). Il dato resta vero ed esatto e occupa al
massimo una slide (problema o why-now); tutto quello che il deck ci costruisce sopra è
inventato. Il disclaimer finale separa il vero dal finto ("Il dato è reale. La startup
no."). Niente notizie tragiche come gancio, in nessun registro.

**Lingua.** Default: italiano. Si deduce dalla richiesta. Se richiesta un'altra lingua,
rigenera dai moduli nella lingua target: il gergo cambia strato (in inglese il buzzword
corporate puro, in italiano l'itanglese), i nomi si rifanno, non si traducono.

### 2. Scegli i moduli

Consulta `references/moduli.md`. Numero di moduli in base al livello:

| Livello | Moduli narrativi (A-E) | Tic formali (F) |
|---------|------------------------|-----------------|
| 1-3 | 1 | nessuno |
| 4-6 | 2 | titoli da manifesto su metà slide |
| 7-8 | 3-4 | + note del presentatore (3-5), eventuale errore piantato |
| 9-10 | 5+ | tutto: titoli, emoji, note su ogni slide, errore piantato, footer paranoico; al 10 l'appendice |

I moduli scelti dall'utente hanno la precedenza; aggiungine altri per arrivare al conto.
Ogni modulo indica in quale slide vive: mettilo lì, non altrove.

### 3. Scrivi il deck

Segui lo scheletro e le regole Marp in `references/struttura-marp.md`: frontmatter
col tema della casa, separatore `---`, classe lead per copertina e slide a frase
singola, commenti HTML come note del presentatore. In bozza ogni immagine è una
descrizione fra parentesi quadre, in corsivo, e la descrizione lavora per il cringe;
in consegna diventa una foto generata (vedi §4). **Mai immagini prese dal web.**

Usa `references/lessico.md` per la fabbrica di nomi (startup e persone), i buzzword,
il gergo VC quasi giusto, le formule per ogni slide e il repertorio dei disclaimer.

**Leva principale del cringe: lo scarto.** Tre scarti, tutti da lavorare: problema
piccolo contro missione cosmica, traction minuscola contro valutazione richiesta,
team di due contro organigramma da multinazionale. Non alzare il livello aggiungendo
emoji ai titoli: alza lo scarto.

**I numeri devono tornare, ma male.** In registro credibile ogni cifra è plausibile
da sola; è mettendole insieme che il lettore attento trova il buco (i +312% che a
conti fatti sono 16 utenti). Al livello 7-8 pianta un solo errore (P32): un dato che
si contraddice fra due slide. Mai due.

**La regola dell'eufemismo.** Se l'idea è di per sé disturbante (un dispositivo
punitivo, un prodotto che ascolta di nascosto, qualcosa che nessuno direbbe ad alta
voce), non esagerare: in registro credibile il deck la tratta con lessico levigato
("feedback aptico correttivo", "copilota conversazionale") e una nota del presentatore
proibisce la parola vera ("Non dire scarica. Mai."). Il deck è tanto più forte quanto
più è composto. Il disclaimer può dirlo: "è una parodia di come un eufemismo fa passare
qualunque cosa".

**Regole fisse del deck.** Valgono sempre, a ogni livello e in ogni registro:

- **Il competitor assurdo.** La matrice della competizione include sempre, accanto
  ai player di categoria, un concorrente che nessuno considererebbe tale ("i nonni",
  "alzare la voce", "il quaderno della spesa", "non fare niente"), trattato con la
  stessa serietà degli altri: colonna nella matrice, ✗ e ✓ compresi. Uno per deck,
  coerente col settore.
- **Le persone hanno sempre doppio nome e doppio cognome** ("Maria Clotilde
  Colombo Brambilla", "Gian Ermenegildo Esposito Marino"), **con il secondo nome
  sempre ottocentesco** (repertorio in `lessico.md`), **e referenze incredibili**
  ma non verificabili: un TEDx in un teatro
  di provincia, migliaia di persone "formate", codice scritto per un progetto
  spaziale europeo (uno stage). Referenza enorme, sostanza minuscola: è la legge
  dello scarto applicata alle bio. Sempre per categoria, mai enti reali.
- **Le proiezioni coprono sempre cinque anni.** I primi quattro crescono con un
  moltiplicatore quasi costante; il quinto è sovrastimato oltre ogni logica
  (×8-×10 sul quarto), come se il founder avesse tirato la riga a mano. Sotto la
  tabella, nella stessa slide, va sempre il grafico che sale (P07): un file SVG
  costruito sui dati delle proiezioni, salvato accanto al deck e referenziato come
  immagine, senza unità sull'asse Y e con l'asterisco "*stima" sull'ultimo punto.
- **Ogni immagine vive in una slide dedicata**, con un titolo da manifesto tutto
  suo ("La sera in cui tutto è cambiato"), mai incastrata sotto il testo di
  un'altra slide. Vale per i placeholder e per le immagini generate.

**Anti-template.** Ask, proiezioni, chiusura e note tendono a uscire uguali da un deck
all'altro. In un giro di più deck (o se l'utente ne ha già ricevuto uno in questa
conversazione) varia: la struttura dell'ask, il moltiplicatore delle proiezioni, la
formula del "già coperto", e **non riusare una nota del presentatore già scritta**.
Repertorio di varianti in `lessico.md`, sezione "Slide ripetitive".

Consulta `references/esempi.md` per sentire come suonano un deck completo di livello
7, gli estratti di livello 9 parodico e surreale, e un livello 4.

### 4. Consegna

Se hai accesso al filesystem, **scrivi il deck in**
`esempi/<nome-startup>/pitch-<nome-startup>.md` nella cartella di lavoro, con le
immagini e l'SVG delle proiezioni in `img/` accanto, e dillo all'utente in una
riga. Se non ce l'hai, mostra il deck in un blocco di codice markdown, così si
copia in un file senza che il rendering mangi i separatori.

**Le immagini.** Se hai l'automazione del browser (Claude in Chrome), genera tu
le foto dei placeholder su gemini.google.com con l'account dell'utente: un prompt
per immagine (fotorealistico, regole in `struttura-marp.md`), scarichi dal
pulsante di download e sposti i file in `img/`. Chiedi l'ok una volta prima del
primo giro. Senza browser, consegna i prompt pronti. L'SVG delle proiezioni
invece lo scrivi sempre tu, sui dati della tabella.

Poi, in due righe, elenca i moduli usati con i loro codici e indica in quale slide sta
l'errore piantato, se c'è.

**Il post LinkedIn companion.** Dopo il deck genera sempre anche il post LinkedIn
del founder, usando la skill `linkedin-cringe` (se disponibile sulla macchina:
cercala fra le skill caricate o in `.claude/skills/` dei repo vicini) e passandole
le informazioni del pitch: stesso livello, stesso registro, la voce del founder,
gli stessi numeri (waitlist, ask, traction), la stessa origin story e lo stesso
eufemismo se c'è. L'errore piantato del post contraddice un numero del deck.
Salvalo come `post-<nome-startup>.md` accanto al deck. Se linkedin-cringe non
c'è, dillo e salta il passo.

Chiudi sempre offrendo un giro successivo: alzare o abbassare il livello, cambiare
voce, rigenerare con altri moduli o le immagini.

Ricorda all'utente, in mezza riga, come renderizzarlo: plugin Marp per VS Code, oppure
`npx @marp-team/marp-cli pitch-x.md --allow-local-files -o pitch-x.pdf`. Se hai una
shell con marp-cli e un Chromium, genera tu il PDF e, prima di consegnarlo, renderizza
le slide in PNG e controlla a occhio quelle con tabelle e immagini: sono quelle che
traboccano.

## Non deve sembrare scritto da un'AI

Un deck che profuma di modello linguistico non è credibile come cringe umano, e il
cringe umano è tutto il punto. Vale a ogni livello e in ogni lingua.

**Vietato in output:**

- **Il trattino lungo.** Mai. Al suo posto: punto, virgola, due punti, parentesi.
- Bullet tutti della stessa lunghezza e della stessa struttura sintattica.
- Le triadi perfette ("non solo X, ma anche Y, e soprattutto Z").
- Le formule da assistente ("è importante notare", "vale la pena sottolineare").
- Lessico uniformemente levigato, senza una sciatteria.

**Obbligatorio, per suonare umani:**

- Almeno una sciatteria per deck in credibile: un titolo in inglese fra titoli
  italiani, "da aggiornare" sotto un grafico, un typo nell'email, "Azienda 1" nel
  mockup.
- Bullet di lunghezza diversa: uno di due parole, uno che va a capo.
- Un dettaglio concreto e inutile: la sede a Rho, il commercialista, l'orario della
  call.
- Ripetere una parola invece di cercare il sinonimo ("scalabile" tre volte va bene).

Eccezione: in registro parodico ai livelli 9-10 la levigatezza da AI può essere essa
stessa un modulo (il founder ha fatto scrivere il deck a un modello e non l'ha
riletto). Va dichiarato all'utente e non si attiva da solo.

## Slide finale di disclaimer

**Sempre presente, sempre l'ultima**, in classe lead, separata dal "Grazie" o
dall'appendice. Rivela lo scherzo. Serve a chi legge e serve all'utente, che decide se
tenerla.

Base: "Questa startup non esiste. Il pattern sì."

**Varia sempre la formulazione** e quando puoi rendila specifica sul deck (ripesca un
numero, un modulo: "I sei C-level sono due persone"). Repertorio in `lessico.md`.

Questa slide è l'unico punto in cui la voce può ammiccare. Le slide sopra restano
rigorosamente serie. La slide dice che è satira; **non spiega la battuta** e in
registro surreale non spiega il sogno.

Con un gancio reale, la slide separa il vero dal finto: "Il dato è reale. La startup
no."

In fondo alla slide, in piccolo e in corsivo, va sempre il link al repository che
ha generato il pitch: `*Generato con [pitch-cringe](https://github.com/matteobaccan/PitchCringe)*`.

Quando consegni, di' all'utente in mezza riga che quella è la slide rimovibile.

## Paletti

Valgono anche in registro credibile, anzi, soprattutto lì:

- **Nessuna startup reale.** Il nome è inventato con le regole della fabbrica di nomi
  (parole composte o storpiate, mai una parola di dizionario). Se un nome ti suona
  familiare, cambialo.
- **Nessuna persona reale**: founder, advisor, investitori, citazioni. Nomi inventati e
  non googlabili; le citazioni motivazionali sono attribuite a "un grande innovatore",
  mai a un nome.
- **Nessuna azienda, fondo, programma, bando o fiera reale** come concorrente, partner,
  investitore o traction. Si citano per categoria ("un fondo di Milano", "una catena
  della GDO", "un programma di accelerazione"). Unica eccezione: i colossi usati come
  termine di paragone in "siamo l'Uber di X" (P03), massimo due per deck, e gli
  strumenti citati come oggetti ("i nostri competitor sono Excel e WhatsApp").
- **Nessun logo.** La griglia dei loghi è sempre una descrizione fra parentesi quadre.
- **Email e domini usano sempre il TLD riservato `.example`** (serenly.example,
  martina@serelny.example): non possono collidere con siti veri, nemmeno per caso.
- **Niente notizie tragiche** come gancio reale, in nessun registro.
- **L'azienda dell'utente non compare mai**, nemmeno con un nome di fantasia che
  potrebbe collidere con aziende vere. Se l'utente vuole un pitch della *sua* startup
  in chiave cringe, usa un nome inventato e diglielo.
- Se l'utente vuole presentarlo davvero a qualcuno, ricordagli una volta che è un deck
  finto, poi fai quello che chiede.
