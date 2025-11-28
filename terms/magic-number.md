# Magic Number

## Cosa significa

Il **Magic Number** (numero magico) è un numero hardcoded nel codice senza spiegazione o contesto. È un code smell che rende il codice difficile da capire e mantenere.

È quello che succede quando vedi `if (status == 42)` e ti chiedi "perché 42?" senza una spiegazione nel codice.

---

## Perché ti serve conoscerlo

Conoscere il termine "Magic Number" ti aiuta a:

- **Riconoscere numeri senza contesto** che rendono il codice poco chiaro
- **Comunicare meglio** con il team: "Questo è un magic number, dovremmo usare una costante"
- **Migliorare la leggibilità** del codice usando costanti descrittive
- **Facilitare la manutenzione** cambiando valori in un solo posto

---

## Come funziona

Il Magic Number si verifica quando:

- **Numeri hardcoded**: Numeri inseriti direttamente nel codice
- **Senza spiegazione**: Nessun commento o costante che spiega il significato
- **Valori magici**: Numeri che hanno un significato specifico ma non evidente
- **Difficile da cambiare**: Se il valore cambia, devi cercarlo in tutto il codice

---

## Esempi comuni

### Esempio 1: Status codes

```php
// Magic number: cosa significa 2?
if ($order->status == 2) {
    // Process order
}

// Meglio: costante descrittiva
const ORDER_STATUS_PROCESSING = 2;
if ($order->status == ORDER_STATUS_PROCESSING) {
    // Process order
}
```

**Problema:** Il numero 2 non comunica il significato.

### Esempio 2: Timeout

```php
// Magic number: perché 30 secondi?
sleep(30);

// Meglio: costante con unità
const TIMEOUT_SECONDS = 30;
sleep(TIMEOUT_SECONDS);
```

**Problema:** Non è chiaro perché 30 secondi.

### Esempio 3: Limiti

```php
// Magic number: perché 100?
if (count($items) > 100) {
    throw new Exception('Too many items');
}

// Meglio: costante descrittiva
const MAX_ITEMS_PER_ORDER = 100;
if (count($items) > MAX_ITEMS_PER_ORDER) {
    throw new Exception('Too many items');
}
```

**Problema:** Il limite non è chiaro e difficile da cambiare.

### Esempio 4: Calcoli

```php
// Magic number: perché 0.20?
$discount = $price * 0.20;

// Meglio: costante con significato
const STANDARD_DISCOUNT_RATE = 0.20;
$discount = $price * STANDARD_DISCOUNT_RATE;
```

**Problema:** Non è chiaro cosa rappresenta 0.20.

---

## Come risolverlo

### 1. Estrai costanti

Sostituisci magic numbers con costanti descrittive:

```php
// Prima: magic number
if ($age > 18) { }

// Dopo: costante
const MIN_ADULT_AGE = 18;
if ($age > MIN_ADULT_AGE) { }
```

### 2. Usa enum o classi costanti

Per valori correlati, usa enum o classi:

```php
// Prima: magic numbers
if ($status == 1) { }
if ($status == 2) { }
if ($status == 3) { }

// Dopo: enum
enum OrderStatus {
    case PENDING = 1;
    case PROCESSING = 2;
    case COMPLETED = 3;
}

if ($status == OrderStatus::PROCESSING) { }
```

### 3. Usa configurazione

Per valori che possono cambiare, usa configurazione:

```php
// Prima: magic number
$timeout = 30;

// Dopo: configurazione
$timeout = config('app.request_timeout', 30);
```

### 4. Documenta il significato

Se devi usare un numero, documentalo:

```php
// Se proprio devi usare un numero, documentalo
// 42 è il codice status per "processing" secondo la specifica API v2
if ($status == 42) { }
```

---

## Prevenzione

- **Costanti descrittive**: Usa sempre costanti per valori significativi
- **Enum**: Usa enum per valori correlati
- **Configurazione**: Usa config per valori che possono cambiare
- **Code review**: Identifica magic numbers durante le review
- **Static analysis**: Usa strumenti che rilevano magic numbers

---

## Origine del termine

Il termine **Magic Number** è stato coniato nella programmazione per descrivere numeri hardcoded senza contesto.

L'analogia con la magia è efficace: così come un numero magico in matematica ha proprietà speciali ma misteriose, un magic number nel codice ha un significato speciale ma non evidente.

---

## Termini correlati

- **Code Smell** - Indicatore di problemi nel codice
- **Hardcoding** - Valori inseriti direttamente nel codice
- **Configuration** - Gestione di valori configurabili

---

## Risorse utili

- [Refactoring.Guru: Magic Number](https://refactoring.guru/replace-magic-number-with-symbolic-constant) - Tecnica di refactoring
- [PHP Enums](https://www.php.net/manual/en/language.enumerations.php) - Enum in PHP 8.1+
- [Laravel Configuration](https://laravel.com/docs/configuration) - Gestione configurazione

