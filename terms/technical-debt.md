# Technical Debt

## Cosa significa

Il **Technical Debt** (debito tecnico) è il costo futuro di dover riscrivere o refactorare codice che è stato scritto velocemente o in modo non ottimale per rispettare scadenze. È un concetto che descrive il compromesso tra velocità di sviluppo e qualità del codice.

È quello che succede quando scegli di scrivere codice velocemente invece di farlo bene, accumulando "debito" che dovrà essere "pagato" in futuro con refactoring o riscritture.

---

## Perché ti serve conoscerlo

Conoscere il termine "Technical Debt" ti aiuta a:

- **Comunicare il costo** di scelte tecniche veloci
- **Pianificare refactoring** per pagare il debito
- **Bilanciare velocità e qualità** nelle decisioni
- **Spiegare ai manager** perché serve tempo per migliorare il codice

---

## Come funziona

Il Technical Debt si accumula quando:

- **Scadenze strette**: Scegli velocità invece di qualità
- **Scelte rapide**: Implementi soluzioni veloci invece di corrette
- **Codice legacy**: Mantieni codice vecchio invece di refactorare
- **Mancanza di test**: Non scrivi test per risparmiare tempo
- **Documentazione mancante**: Non documenti per andare più veloce

---

## Esempi comuni

### Esempio 1: Codice veloce invece di corretto

```php
// Technical debt: codice veloce ma problematico
public function processOrder($orderId) {
    $order = Order::find($orderId);
    $order->status = 'processed';
    $order->save();
    
    // Debito: nessuna validazione, nessun test, nessuna gestione errori
    // Dovrà essere refactorato in futuro
}
```

**Debito:** Codice funziona ma manca validazione, test, gestione errori.

### Esempio 2: Duplicazione invece di astrazione

```php
// Technical debt: codice duplicato invece di astrazione
public function createUser($data) {
    // Logica duplicata
}

public function updateUser($id, $data) {
    // Stessa logica duplicata
}

// Debito: quando la logica cambia, devi cambiare in 2 posti
// Dovrà essere refactorato per estrarre logica comune
```

**Debito:** Duplicazione che richiederà refactoring.

### Esempio 3: Nessun test

```php
// Technical debt: nessun test scritto
public function calculateTotal($items) {
    // Logica complessa senza test
    // Debito: difficile da modificare senza rompere qualcosa
}
```

**Debito:** Mancanza di test rende difficile modificare il codice.

---

## Come gestirlo

### 1. Riconosci il debito

Documenta il debito tecnico:

```php
// TODO: Refactor this - technical debt
// Issue: #123
// Reason: Written quickly for deadline
// Cost: High - affects multiple features
```

### 2. Pianifica il pagamento

Pianifica quando pagare il debito:

```markdown
## Technical Debt Backlog
- [ ] Refactor OrderProcessor (2 giorni)
- [ ] Aggiungere test per PaymentService (1 giorno)
- [ ] Documentare API (1 giorno)
```

### 3. Paga regolarmente

Dedica tempo regolare per pagare il debito:

```markdown
## Sprint Planning
- 70% nuove feature
- 20% technical debt
- 10% bug fix
```

### 4. Evita nuovo debito

Cerca di non accumulare nuovo debito:

```php
// Invece di: codice veloce
// Scrivi: codice corretto (anche se più lento)
```

---

## Prevenzione

- **Code review**: Identifica debito durante le review
- **Test**: Scrivi test per evitare debito futuro
- **Refactoring continuo**: Migliora il codice regolarmente
- **Documentazione**: Documenta per evitare debito di conoscenza
- **Architettura**: Progetta architettura che evita debito

---

## Origine del termine

Il termine **Technical Debt** è stato coniato da **Ward Cunningham** nel 1992.

L'analogia con il debito finanziario è efficace: così come un prestito ti permette di comprare qualcosa ora ma devi pagarlo con interessi in futuro, il debito tecnico ti permette di sviluppare velocemente ora ma devi "pagarlo" con refactoring in futuro.

---

## Termini correlati

- **Code Smell** - Indicatore di problemi nel codice
- **Legacy Code** - Codice vecchio che crea debito
- **Refactoring** - Processo per pagare il debito

---

## Risorse utili

- [Ward Cunningham: Technical Debt](https://www.youtube.com/watch?v=pqeJffwnpcY) - Video originale
- [Martin Fowler: Technical Debt](https://martinfowler.com/bliki/TechnicalDebt.html) - Articolo approfondito
- [Laravel Best Practices](https://laravel.com/docs) - Best practices Laravel

