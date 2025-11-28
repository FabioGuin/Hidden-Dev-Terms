# Analysis Paralysis

## Cosa significa

L'**Analysis Paralysis** (paralisi da analisi) è la situazione in cui un team o una persona analizza un problema così a fondo che non riesce mai a prendere una decisione o iniziare a implementare. È l'opposto della premature optimization.

È quello che succede quando analizzi tutto all'infinito, crei documenti, diagrammi, e discussioni, ma non implementi mai nulla.

---

## Perché ti serve conoscerlo

Conoscere il termine "Analysis Paralysis" ti aiuta a:

- **Riconoscere quando stai analizzando troppo** invece di agire
- **Comunicare meglio** con il team: "Stiamo facendo analysis paralysis, iniziamo a implementare"
- **Bilanciare analisi e azione** nelle decisioni
- **Evitare perfezionismo** che blocca il progresso

---

## Come funziona

L'Analysis Paralysis si verifica quando:

- **Troppa analisi**: Analizzi ogni possibile scenario
- **Paura di sbagliare**: Non vuoi prendere decisioni sbagliate
- **Perfezionismo**: Vuoi la soluzione perfetta prima di iniziare
- **Mancanza di dati**: Aspetti dati che non arriveranno mai
- **Overthinking**: Pensi troppo invece di agire

---

## Esempi comuni

### Esempio 1: Troppa pianificazione

```
Team analizza per settimane:
- Documenti di requisiti
- Diagrammi UML
- Architettura dettagliata
- Design patterns
- Ma non implementa mai nulla
```

**Problema:** Troppa analisi, zero implementazione.

### Esempio 2: Aspettare dati perfetti

```php
// Analysis paralysis: aspetti dati perfetti
// "Non possiamo iniziare finché non abbiamo tutti i requisiti"
// "Aspettiamo il feedback del cliente"
// "Dobbiamo analizzare tutti i casi edge"
// Risultato: non inizi mai
```

**Problema:** Aspetti condizioni perfette che non arriveranno mai.

### Esempio 3: Overthinking

```php
// Analysis paralysis: pensi troppo
// "Quale pattern usare? Strategy? Factory? Command?"
// "Quale architettura? MVC? Hexagonal? Clean?"
// "Quale database? MySQL? PostgreSQL? MongoDB?"
// Risultato: non decidi mai
```

**Problema:** Troppe opzioni, nessuna decisione.

---

## Come evitarlo

### 1. Time-boxing

Limita il tempo per l'analisi:

```
"Analizziamo per 2 giorni, poi decidiamo e implementiamo"
```

### 2. Prototipo rapido

Crea prototipi invece di analizzare:

```php
// Invece di: analizzare per settimane
// Fai: prototipo rapido in 1 giorno
$prototype = new FeaturePrototype();
$prototype->test();
```

### 3. Decisioni reversibili

Prendi decisioni che puoi cambiare:

```php
// Decisione reversibile: puoi cambiare dopo
// Inizia con soluzione semplice, migliora dopo
```

### 4. Fail fast

Fallisci velocemente e impara:

```php
// Invece di: analizzare per evitare errori
// Fai: implementa, testa, impara, migliora
```

---

## Prevenzione

- **Time-boxing**: Limita tempo per analisi
- **Prototipi**: Crea prototipi invece di analizzare
- **Decisioni reversibili**: Prendi decisioni che puoi cambiare
- **Fail fast**: Fallisci velocemente e impara
- **MVP**: Inizia con Minimum Viable Product

---

## Origine del termine

Il termine **Analysis Paralysis** deriva dalla gestione aziendale e descrive la situazione in cui troppa analisi porta a paralisi decisionale.

---

## Termini correlati

- **Premature Optimization** - Ottimizzare troppo presto (opposto)
- **Bikeshedding** - Perdere tempo su dettagli
- **Yak Shaving** - Task irrilevanti

---

## Risorse utili

- [Wikipedia: Analysis Paralysis](https://en.wikipedia.org/wiki/Analysis_paralysis) - Articolo Wikipedia
- [Laravel Quick Start](https://laravel.com/docs) - Inizia velocemente
