# Hidden Dev Terms
> Termini informatici poco conosciuti che descrivono fenomeni di pratica "programmesca" quotidiana

Questa repository raccoglie termini tecnici e slang informatico che descrivono fenomeni comuni nella pratica quotidiana dello sviluppo, ma che spesso non hanno un nome conosciuto. Quando questi fenomeni accadono, li descriviamo con termini inventati o coloriti, senza sapere che esiste già un termine preciso.

---

## Indice

- [Bug e Debugging](#bug-e-debugging)
  - [Heisenbug](#heisenbug)
  - [Schrödinbug](#schrödinbug)
  - [Bohrbug](#bohrbug)
  - [Mandelbug](#mandelbug)
  - [Rubber Duck Debugging](#rubber-duck-debugging)
- [Problemi di Codice](#problemi-di-codice)
  - [Code Smell](#code-smell)
  - [God Object](#god-object)
  - [Magic Number](#magic-number)
  - [Spaghetti Code](#spaghetti-code)
  - [Dead Code](#dead-code)
  - [Zombie Code](#zombie-code)
  - [Ninja Comment](#ninja-comment)
- [Processi e Metodologie](#processi-e-metodologie)
  - [Bikeshedding](#bikeshedding)
  - [Yak Shaving](#yak-shaving)
  - [Premature Optimization](#premature-optimization)
  - [Technical Debt](#technical-debt)
  - [Analysis Paralysis](#analysis-paralysis)
  - [Feature Creep](#feature-creep)
  - [Scope Creep](#scope-creep)
  - [Cargo Cult Programming](#cargo-cult-programming)
  - [Golden Hammer](#golden-hammer)
  - [Not Invented Here (NIH) Syndrome](#not-invented-here-nih-syndrome)
- [Team e Organizzazione](#team-e-organizzazione)
  - [Bus Factor](#bus-factor)
- [Encoding e Caratteri](#encoding-e-caratteri)
  - [Mojibake](#mojibake)
- [Tipizzazione e Pattern](#tipizzazione-e-pattern)
  - [Duck Typing](#duck-typing)
- [Laravel e ORM](#laravel-e-orm)
  - [N+1 Problem](#n1-problem)

---

## Bug e Debugging

### [Heisenbug](./terms/heisenbug.md)

Il **Heisenbug** è un bug che scompare o cambia comportamento quando cerchi di debuggarlo o osservarlo. Il nome deriva dal principio di indeterminazione di Heisenberg in fisica quantistica.

**Esempio:** Un bug funziona in produzione ma fallisce quando aggiungi un `console.log` per debuggarlo, perché il log cambia il timing dell'esecuzione.

### [Schrödinbug](./terms/schroedinbug.md)

Il **Schrödinbug** è un bug che non si manifesta finché qualcuno non lo nota o legge il codice che lo contiene. Una volta notato, inizia a manifestarsi sempre. Il nome deriva dal paradosso del gatto di Schrödinger.

**Esempio:** Un bug esiste nel codice da mesi senza problemi, ma dopo una code review che lo nota, inizia a manifestarsi sempre perché ora tutti lo cercano e lo testano.

### [Bohrbug](./terms/bohrbug.md)

Il **Bohrbug** è un bug che si comporta sempre nello stesso modo, rendendolo facile da riprodurre e debuggare. È l'opposto di un Heisenbug. Il nome deriva dal modello atomico di Bohr.

**Esempio:** Un bug di divisione per zero si manifesta sempre nelle stesse condizioni, rendendolo facile da identificare e fixare.

### [Mandelbug](./terms/mandelbug.md)

Il **Mandelbug** è un bug così complesso che il suo comportamento sembra caotico e imprevedibile, anche se tecnicamente deterministico. Il nome deriva dall'insieme di Mandelbrot.

**Esempio:** Un bug che dipende da molte variabili (timing, stato condiviso, cache) e sembra comportarsi in modo casuale anche se è deterministico.

### [Rubber Duck Debugging](./terms/rubber-duck-debugging.md)

Il **Rubber Duck Debugging** è una tecnica di debugging dove spieghi il problema a un oggetto inanimato (come una papera di gomma) per capirlo meglio. Spesso, durante la spiegazione, capisci la soluzione.

**Esempio:** Sei bloccato su un bug, inizi a spiegare il problema ad alta voce passo per passo, e durante la spiegazione capisci dove sta il problema.

---

## Problemi di Codice

### [Code Smell](./terms/code-smell.md)

Il **Code Smell** è un indicatore di un problema potenziale nel codice. Non è un bug vero e proprio, ma un segnale che qualcosa potrebbe essere sbagliato o che il codice potrebbe essere migliorato.

**Esempio:** Un metodo troppo lungo, codice duplicato, o nomi poco chiari sono code smell che indicano problemi potenziali.

### [God Object](./terms/god-object.md)

Il **God Object** è una classe che sa e fa troppe cose, violando il principio di responsabilità singola. È un code smell comune che indica che una classe ha troppe responsabilità.

**Esempio:** Una classe User che gestisce autenticazione, ordini, pagamenti, notifiche e tutto il resto invece di avere responsabilità separate.

### [Magic Number](./terms/magic-number.md)

Il **Magic Number** è un numero hardcoded nel codice senza spiegazione o contesto. È un code smell che rende il codice difficile da capire e mantenere.

**Esempio:** `if (status == 42)` senza sapere cosa significa 42, invece di usare una costante descrittiva come `ORDER_STATUS_PROCESSING`.

### [Spaghetti Code](./terms/spaghetti-code.md)

Lo **Spaghetti Code** è codice intrecciato, difficile da seguire e mantenere. Il nome deriva dall'analogia con gli spaghetti: così come gli spaghetti sono intrecciati, il codice è intrecciato e difficile da capire.

**Esempio:** Codice con troppi if annidati, goto, o logica così intrecciata che è difficile capire cosa fa e come funziona.

### [Dead Code](./terms/dead-code.md)

Il **Dead Code** è codice che non viene mai eseguito ma è ancora presente nel progetto. Può essere codice commentato, funzioni mai chiamate, o branch di codice inaccessibili.

**Esempio:** Funzioni vecchie mai chiamate, codice commentato che non serve più, o branch di codice che non possono essere raggiunti.

### [Zombie Code](./terms/zombie-code.md)

Lo **Zombie Code** è codice che dovrebbe essere morto (non più necessario) ma continua a essere eseguito, causando problemi o comportamenti inaspettati. A differenza del Dead Code, lo Zombie Code è ancora attivo.

**Esempio:** Codice deprecato ancora chiamato, feature flag vecchi ancora attivi, o codice legacy che interferisce con il nuovo codice.

### [Ninja Comment](./terms/ninja-comment.md)

Il **Ninja Comment** è un commento nel codice che spiega perché qualcosa non funziona o perché è stato fatto in un modo strano, invece di fixare il problema. Il nome deriva dal fatto che questi commenti "appaiono" quando meno te lo aspetti.

**Esempio:** `// TODO: questo non funziona ma non so perché` invece di fixare il problema, o commenti che documentano workaround invece di risolvere la causa.

---

## Processi e Metodologie

### [Bikeshedding](./terms/bikeshedding.md)

Il **Bikeshedding** è la tendenza a perdere tempo su decisioni banali mentre si ignorano decisioni importanti e complesse. Deriva da una storia su un comitato che discute a lungo il colore del capannone delle biciclette mentre approva rapidamente un reattore nucleare.

**Esempio:** Il team discute per 2 ore su nomi di variabili o formattazione del codice, mentre ignora problemi architetturali o decisioni tecniche critiche.

### [Yak Shaving](./terms/yak-shaving.md)

Lo **Yak Shaving** è il fenomeno per cui devi completare una serie apparentemente infinita di task irrilevanti per raggiungere un obiettivo originale. Il nome deriva da una storia dove per comprare una spazzola per il cane, devi prima tosare uno yak.

**Esempio:** Per fixare un bug devi aggiornare le dipendenze, che richiedono un aggiornamento di PHP, che richiede un aggiornamento del sistema operativo, e così via, senza mai arrivare a fixare il bug originale.

### [Premature Optimization](./terms/premature-optimization.md)

La **Premature Optimization** è l'atto di ottimizzare il codice prima che sia necessario o prima di avere dati che dimostrino che l'ottimizzazione è necessaria. È un anti-pattern comune che può rendere il codice più complesso senza benefici reali.

**Esempio:** Aggiungi cache, query complesse, o micro-ottimizzazioni senza misurare se servono, rendendo il codice più complesso senza benefici reali.

### [Technical Debt](./terms/technical-debt.md)

Il **Technical Debt** è il costo futuro di dover riscrivere o refactorare codice che è stato scritto velocemente o in modo non ottimale per rispettare scadenze. È un concetto che descrive il compromesso tra velocità di sviluppo e qualità del codice.

**Esempio:** Scrivi codice velocemente senza test, validazione, o gestione errori per rispettare una scadenza, accumulando "debito" che dovrà essere "pagato" in futuro con refactoring.

### [Analysis Paralysis](./terms/analysis-paralysis.md)

L'**Analysis Paralysis** è la situazione in cui un team o una persona analizza un problema così a fondo che non riesce mai a prendere una decisione o iniziare a implementare. È l'opposto della premature optimization.

**Esempio:** Analizzi tutto all'infinito, crei documenti, diagrammi, e discussioni, ma non implementi mai nulla perché aspetti la soluzione perfetta.

### [Feature Creep](./terms/feature-creep.md)

Il **Feature Creep** è il fenomeno per cui un progetto accumula continuamente nuove funzionalità oltre lo scope originale, rendendolo più complesso e difficile da completare.

**Esempio:** Aggiungi funzionalità "tanto ci siamo" durante lo sviluppo, allontanandoti dall'obiettivo originale e rendendo il progetto più complesso.

### [Scope Creep](./terms/scope-creep.md)

Lo **Scope Creep** è il fenomeno per cui lo scope di un progetto si allarga continuamente oltre i requisiti originali, rendendo il progetto più complesso e difficile da completare.

**Esempio:** I requisiti cambiano continuamente, il cliente chiede nuove funzionalità, e lo scope si allarga oltre i requisiti originali.

### [Cargo Cult Programming](./terms/cargo-cult-programming.md)

Il **Cargo Cult Programming** è la pratica di copiare codice o pattern senza capire perché funzionano. Il nome deriva dai "cargo cult" del Pacifico che imitavano rituali senza capirne il significato.

**Esempio:** Copi codice da Stack Overflow senza capire perché funziona, o usi pattern senza sapere quando servono.

### [Golden Hammer](./terms/golden-hammer.md)

Il **Golden Hammer** è un anti-pattern dove una persona o team usa sempre lo stesso strumento, tecnologia o soluzione per ogni problema, indipendentemente dal fatto che sia appropriato. Deriva dal detto: "Quando hai un martello, tutto sembra un chiodo".

**Esempio:** Usi sempre Laravel per tutto, anche quando non serve, o sempre lo stesso pattern anche quando non è appropriato.

### [Not Invented Here (NIH) Syndrome](./terms/not-invented-here.md)

Il **Not Invented Here (NIH) Syndrome** è la tendenza a rifiutare soluzioni, librerie o codice esistenti e preferire scrivere tutto da zero, anche quando esistono soluzioni mature e testate.

**Esempio:** Invece di usare Guzzle per le chiamate HTTP, riscrivi un client HTTP da zero perché "preferisci controllare tutto tu", anche se Guzzle è maturo, testato e mantenuto.

---

## Team e Organizzazione

### [Bus Factor](./terms/bus-factor.md)

Il **Bus Factor** è una metrica che misura quante persone devono essere investite da un bus (o lasciare il team) prima che il progetto sia a rischio. È una misura della conoscenza condivisa nel team e della dipendenza da singole persone.

**Esempio:** Solo una persona sa come funziona una parte critica del sistema, e se quella persona se ne va, il progetto è in pericolo (Bus Factor 1 = rischio alto).

---

## Encoding e Caratteri

### [Mojibake](./terms/mojibake.md)

Il **Mojibake** (文字化け) è il fenomeno per cui i caratteri vengono visualizzati in modo corrotto a causa di problemi di encoding. Letteralmente significa "caratteri trasformati" in giapponese.

**Esempio:** "Buongiorno" diventa "Ã¨ una bella giornata" quando un file è salvato con UTF-8 ma letto con ISO-8859-1.

---

## Tipizzazione e Pattern

### [Duck Typing](./terms/duck-typing.md)

Il **Duck Typing** è un principio di programmazione dove il tipo di un oggetto è determinato dal suo comportamento (metodi e proprietà) piuttosto che dalla sua classe. Il nome deriva dal detto: "Se cammina come una papera e starnazza come una papera, allora è una papera".

**Esempio:** Controlli se un oggetto ha certi metodi invece di controllare se è di una certa classe, rendendo il codice più flessibile.

---

## Laravel e ORM

### [N+1 Problem](./terms/n-plus-one-problem.md)

Il **N+1 Problem** è un problema di performance comune quando si caricano dati relazionali. Si verifica quando esegui 1 query per ottenere N record, e poi N query aggiuntive (una per ogni record) per caricare le relazioni. Il risultato è N+1 query invece di 2 query ottimizzate.

**Esempio:** Carichi 100 utenti con 1 query, poi fai 100 query separate per caricare gli ordini di ogni utente, invece di usare eager loading con 2 query totali.

---

