# Bikeshedding

## Cosa significa

Il **Bikeshedding** (o "Parkinson's Law of Triviality") è la tendenza a perdere tempo su decisioni banali mentre si ignorano decisioni importanti e complesse. Il termine deriva da una storia satirica su un comitato che discute a lungo il colore del capannone delle biciclette mentre approva rapidamente un reattore nucleare.

È quello che succede quando il team discute per ore su nomi di variabili, formattazione del codice, o scelte minori, mentre ignora problemi architetturali o decisioni tecniche critiche.

---

## Perché ti serve conoscerlo

Conoscere il termine "Bikeshedding" ti aiuta a:

- **Riconoscere quando stai perdendo tempo** su decisioni banali
- **Focalizzarti sulle decisioni importanti** invece di quelle facili
- **Comunicare meglio** con il team: "Stiamo facendo bikeshedding, concentriamoci sul problema principale"
- **Migliorare le riunioni** evitando discussioni infinite su dettagli irrilevanti

---

## Come funziona

Il Bikeshedding si verifica perché:

- **Decisioni semplici** sono facili da capire e discutere (tutti hanno un'opinione)
- **Decisioni complesse** richiedono competenze specifiche (pochi possono contribuire)
- **Sensazione di progresso**: discutere dettagli dà l'impressione di fare qualcosa
- **Evitare responsabilità**: è più facile discutere dettagli che prendere decisioni difficili

---

## Esempi comuni

### Esempio 1: Discussione infinita su nomi

```php
// Team discute per 2 ore su quale nome usare:
class UserManager { }
class UserService { }
class UserHandler { }
class UserController { } // <-- Ma non è un controller HTTP!

// Mentre ignora il problema: la classe fa troppe cose
```

**Problema reale:** La classe viola il Single Responsibility Principle, ma il team discute solo il nome.

### Esempio 2: Formattazione del codice

```
Team discute per 1 ora:
- Spazi vs Tab
- 2 vs 4 spazi
- Punto e virgola sì o no

Mentre ignora:
- Architettura del progetto
- Performance critiche
- Sicurezza
```

**Problema reale:** Il team perde tempo su formattazione invece di usare un formatter automatico.

### Esempio 3: Code review su dettagli

```php
// Review commento:
"Perché hai usato 'get' invece di 'fetch'?"

// Mentre ignora:
- Nessun test
- Logica business complessa non documentata
- Potenziali bug di sicurezza
```

**Problema reale:** Il reviewer si concentra su dettagli stilistici invece di problemi reali.

---

## Come evitarlo

### 1. Stabilisci priorità

Identifica le decisioni importanti e concentrati su quelle:

```markdown
## Priorità Alta
- Architettura
- Sicurezza
- Performance critiche

## Priorità Bassa
- Nomi di variabili
- Formattazione
- Stile del codice
```

### 2. Usa convenzioni e standard

Stabilisci standard condivisi per evitare discussioni:

```php
// .php-cs-fixer.php - Formattazione automatica
// PSR-12 standard - Nessuna discussione necessaria
```

### 3. Time-boxing

Limita il tempo per decisioni banali:

```
"Discutiamo il nome per massimo 5 minuti, poi decidiamo e andiamo avanti"
```

### 4. Focus su impatto

Valuta l'impatto delle decisioni:

```
Alta impatto = più tempo
Bassa impatto = decisione rapida
```

### 5. Delegazione

Delega decisioni banali a una persona o a uno standard:

```
"Usa PSR-12 per formattazione, non discutiamo"
```

---

## Quando è accettabile

Non tutto il bikeshedding è negativo:

- **Standardizzazione**: Discutere standard del team è utile
- **Onboarding**: Aiuta i nuovi membri a capire le convenzioni
- **Team building**: A volte le discussioni leggere aiutano il team a conoscersi

Il problema è quando diventa la norma invece dell'eccezione.

---

## Origine del termine

Il termine **Bikeshedding** deriva da una storia satirica di **C. Northcote Parkinson** nel libro "Parkinson's Law" (1957).

La storia racconta di un comitato che deve approvare:
1. **Reattore nucleare** (complesso, costoso) → Approvato in 2 minuti
2. **Capannone biciclette** (semplice, economico) → Discussione di 45 minuti sul colore

Tutti possono avere un'opinione sul colore del capannone, ma pochi capiscono i reattori nucleari.

Il termine è anche noto come **"Parkinson's Law of Triviality"**.

---

## Termini correlati

- **Yak Shaving** - Fare task irrilevanti per raggiungere un obiettivo
- **Analysis Paralysis** - Paralisi da troppa analisi
- **Premature Optimization** - Ottimizzare prima del necessario

---

## Risorse utili

- [Wikipedia: Parkinson's Law of Triviality](https://en.wikipedia.org/wiki/Law_of_triviality)
- [The Bikeshed Effect](https://www.freebsd.org/doc/en/articles/mailing-list-faq/bikeshed.html) - Articolo originale
- [Laravel Coding Standards](https://laravel.com/docs/contributions#coding-standards) - Standard per evitare bikeshedding

