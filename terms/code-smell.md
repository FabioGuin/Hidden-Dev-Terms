# Code Smell

## Cosa significa

Il **Code Smell** (puzza di codice) è un indicatore di un problema potenziale nel codice. Non è un bug vero e proprio, ma un segnale che qualcosa potrebbe essere sbagliato o che il codice potrebbe essere migliorato.

È quello che succede quando guardi il codice e pensi "questo codice puzza" - qualcosa non va, anche se tecnicamente funziona.

---

## Perché ti serve conoscerlo

Conoscere il termine "Code Smell" ti aiuta a:

- **Riconoscere problemi potenziali** prima che diventino bug veri
- **Comunicare meglio** con il team: "Questo codice ha un code smell"
- **Migliorare la qualità** del codice identificando aree da refactorare
- **Prevenire problemi futuri** risolvendo i code smell prima che peggiorino

---

## Come funziona

Il Code Smell si verifica quando:

- **Codice funziona ma è sospetto**: Il codice funziona ma qualcosa non va
- **Violazione di principi**: Il codice viola principi di design (SOLID, DRY, KISS)
- **Difficile da mantenere**: Il codice è difficile da capire o modificare
- **Pattern sospetti**: Il codice mostra pattern che indicano problemi futuri

---

## Esempi comuni

### Esempio 1: Metodo troppo lungo

```php
// Code smell: metodo troppo lungo (200+ righe)
public function processOrder($orderId) {
    // 50 righe di validazione
    // 50 righe di calcolo
    // 50 righe di aggiornamento database
    // 50 righe di invio email
    // Difficile da testare, capire, e mantenere
}
```

**Problema:** Il metodo fa troppe cose ed è difficile da mantenere.

### Esempio 2: Duplicazione

```php
// Code smell: codice duplicato
public function calculateTotal($items) {
    $total = 0;
    foreach ($items as $item) {
        $total += $item->price * $item->quantity;
    }
    return $total;
}

public function calculateSubtotal($items) {
    $total = 0;
    foreach ($items as $item) {
        $total += $item->price * $item->quantity; // Duplicato!
    }
    return $total;
}
```

**Problema:** Violazione del principio DRY (Don't Repeat Yourself).

### Esempio 3: Magic numbers

```php
// Code smell: numeri magici senza spiegazione
if ($user->age > 18 && $user->age < 65) {
    // Perché 18? Perché 65?
}

// Meglio:
const MIN_ADULT_AGE = 18;
const MAX_RETIREMENT_AGE = 65;

if ($user->age > MIN_ADULT_AGE && $user->age < MAX_RETIREMENT_AGE) {
}
```

**Problema:** Numeri hardcoded senza contesto.

### Esempio 4: Nomi poco chiari

```php
// Code smell: nomi poco descrittivi
public function doStuff($data) {
    // Cosa fa questa funzione?
}

// Meglio:
public function calculateOrderTotal(OrderData $orderData): float {
    // Chiaro cosa fa
}
```

**Problema:** Nomi che non comunicano l'intento.

---

## Come risolverlo

### 1. Refactoring

Ristruttura il codice per eliminare il code smell:

```php
// Prima: metodo troppo lungo
public function processOrder($orderId) {
    // 200 righe
}

// Dopo: metodi separati
public function processOrder($orderId) {
    $this->validateOrder($orderId);
    $this->calculateTotal($orderId);
    $this->updateInventory($orderId);
    $this->sendConfirmation($orderId);
}
```

### 2. Estrai costanti

Sostituisci magic numbers con costanti:

```php
// Prima
if ($age > 18) { }

// Dopo
const MIN_ADULT_AGE = 18;
if ($age > MIN_ADULT_AGE) { }
```

### 3. Elimina duplicazione

Estrai codice comune in metodi riutilizzabili:

```php
// Prima: duplicato
public function calculateTotal($items) { /* ... */ }
public function calculateSubtotal($items) { /* ... */ }

// Dopo: metodo condiviso
private function sumItemPrices($items) { /* ... */ }
public function calculateTotal($items) {
    return $this->sumItemPrices($items) + $this->getTax($items);
}
```

### 4. Migliora i nomi

Usa nomi descrittivi che comunicano l'intento:

```php
// Prima
public function doStuff($data) { }

// Dopo
public function processPayment(PaymentData $paymentData): PaymentResult { }
```

---

## Prevenzione

- **Code review**: Identifica code smell durante le review
- **Static analysis**: Usa strumenti come PHPStan o Psalm
- **Test**: Scrivi test che rivelano code smell
- **Refactoring continuo**: Migliora il codice regolarmente
- **Principi SOLID**: Segui i principi di design

---

## Origine del termine

Il termine **Code Smell** è stato coniato da **Kent Beck** e reso popolare da **Martin Fowler** nel libro "Refactoring" (1999).

L'analogia con l'odore è efficace: così come un cattivo odore indica un problema (anche se non sempre visibile), un code smell indica un problema nel codice (anche se non sempre un bug).

---

## Termini correlati

- **Refactoring** - Processo di miglioramento del codice
- **Technical Debt** - Debito tecnico accumulato
- **God Object** - Classe che fa troppe cose (code smell specifico)

---

## Risorse utili

- [Refactoring.Guru: Code Smells](https://refactoring.guru/smells) - Catalogo completo di code smell
- [Martin Fowler: Code Smell](https://martinfowler.com/bliki/CodeSmell.html) - Articolo originale
- [PHPStan](https://phpstan.org/) - Static analysis per PHP
- [Laravel Best Practices](https://laravel.com/docs) - Best practices Laravel

