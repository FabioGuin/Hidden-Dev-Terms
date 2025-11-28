# Schrödinbug

## Cosa significa

Il **Schrödinbug** è un bug che non si manifesta finché qualcuno non lo nota o legge il codice che lo contiene. Una volta notato, inizia a manifestarsi sempre. Il nome deriva dal paradosso del gatto di Schrödinger in fisica quantistica, dove un sistema esiste in uno stato indeterminato finché non viene osservato.

È quello che succede quando un bug esiste nel codice da mesi, ma nessuno se ne accorge finché qualcuno non legge quella parte del codice o ne parla. Poi, magicamente, il bug inizia a manifestarsi sempre.

---

## Perché ti serve conoscerlo

Conoscere il termine "Schrödinbug" ti aiuta a:

- **Riconoscere bug nascosti** che esistono ma non si manifestano
- **Comunicare meglio** con il team: "Abbiamo un Schrödinbug, esiste ma non si manifesta ancora"
- **Capire perché** un bug inizia a manifestarsi dopo che è stato notato
- **Prevenire bug** attraverso code review e test approfonditi

---

## Come funziona

Il Schrödinbug si verifica quando:

- **Bug esistente ma non attivo**: Il bug esiste nel codice ma le condizioni per attivarlo non si verificano
- **Osservazione cambia il comportamento**: Leggere o modificare il codice cambia inconsciamente il comportamento
- **Effetto placebo negativo**: Una volta notato, si inizia a cercare il bug e lo si trova sempre
- **Cambiamenti inconsci**: Modifiche al codice durante il debugging attivano il bug

---

## Esempi comuni

### Esempio 1: Bug che appare dopo code review

```php
// Codice che esiste da 6 mesi, nessun problema

public function calculateTotal($items) {
    $total = 0;
    foreach ($items as $item) {
        $total += $item->price; // Bug: non gestisce null
    }
    return $total;
}

// Dopo code review che nota il problema:
// Il bug inizia a manifestarsi sempre
```

**Causa:** Il reviewer ha notato il problema, ora tutti lo cercano e lo trovano.

### Esempio 2: Bug che appare dopo documentazione

```javascript
// Funzione che funziona da sempre

function processData(data) {
    // Bug: non gestisce array vuoti
    return data.map(item => item.value);
}

// Dopo aver documentato la funzione:
// Il bug inizia a manifestarsi con array vuoti
```

**Causa:** Documentare la funzione ha fatto notare il caso edge, ora viene testato e il bug appare.

### Esempio 3: Bug che appare dopo refactoring

```php
// Codice legacy che funziona

public function getUser($id) {
    return User::find($id); // Bug: non gestisce id null
}

// Dopo refactoring per "migliorare" il codice:
// Il bug inizia a manifestarsi
```

**Causa:** Il refactoring ha cambiato inconsciamente il comportamento o ha esposto il bug.

---

## Come risolverlo

### 1. Code review approfondite

Fai code review che cercano attivamente potenziali bug:

```php
// Durante code review, chiedi:
// - Cosa succede se $data è null?
// - Cosa succede se l'array è vuoto?
// - Cosa succede se la connessione fallisce?
```

### 2. Test edge cases

Scrivi test per casi limite:

```php
test('handles null input', function () {
    expect(calculateTotal(null))->toThrow(Exception::class);
});

test('handles empty array', function () {
    expect(calculateTotal([]))->toBe(0);
});
```

### 3. Static analysis

Usa strumenti di analisi statica per trovare bug potenziali:

```bash
# PHPStan
vendor/bin/phpstan analyse

# Psalm
vendor/bin/psalm
```

### 4. Monitoring e logging

Monitora il codice in produzione per trovare bug nascosti:

```php
// Laravel
Log::warning('Potential bug detected', [
    'data' => $data,
    'context' => 'calculateTotal'
]);
```

---

## Prevenzione

- **Test completi**: Scrivi test per tutti i casi edge
- **Code review**: Fai review approfondite che cercano bug
- **Static analysis**: Usa strumenti automatici per trovare bug
- **Documentazione**: Documenta i casi edge e le assunzioni
- **Defensive programming**: Scrivi codice che gestisce tutti i casi

---

## Origine del termine

Il termine **Schrödinbug** deriva dal paradosso del gatto di **Erwin Schrödinger** in fisica quantistica.

Nel paradosso, un gatto in una scatola esiste in uno stato di sovrapposizione (vivo e morto) finché la scatola non viene aperta e osservata. Allo stesso modo, un Schrödinbug esiste in uno stato indeterminato (bug e non-bug) finché non viene osservato.

Il termine è stato coniato nella comunità di sviluppo per descrivere questo comportamento strano dei bug.

---

## Termini correlati

- **Heisenbug** - Bug che scompare quando cerchi di debuggarlo
- **Bohrbug** - Bug che si comporta sempre nello stesso modo
- **Mandelbug** - Bug così complesso che il suo comportamento sembra caotico

---

## Risorse utili

- [Wikipedia: Schrödinbug](https://en.wikipedia.org/wiki/Heisenbug#Schr%C3%B6dinbug)
- [PHPStan](https://phpstan.org/) - Static analysis per PHP
- [Laravel Testing](https://laravel.com/docs/testing) - Guida ai test Laravel

