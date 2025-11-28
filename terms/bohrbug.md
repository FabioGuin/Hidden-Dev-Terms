# Bohrbug

## Cosa significa

Il **Bohrbug** è un bug che si comporta sempre nello stesso modo, rendendolo facile da riprodurre e debuggare. È l'opposto di un Heisenbug. Il nome deriva dal modello atomico di Bohr, dove gli elettroni seguono orbite prevedibili e deterministiche.

È quello che succede quando un bug è affidabile, riproducibile e prevedibile: ogni volta che esegui il codice nelle stesse condizioni, ottieni lo stesso errore.

---

## Perché ti serve conoscerlo

Conoscere il termine "Bohrbug" ti aiuta a:

- **Riconoscere bug facili da debuggare** che si comportano in modo prevedibile
- **Comunicare meglio** con il team: "Abbiamo un Bohrbug, è facile da riprodurre"
- **Apprezzare i bug prevedibili** invece di lamentarti dei bug difficili
- **Distinguere** tra bug deterministici (Bohrbug) e bug non deterministici (Heisenbug)

---

## Come funziona

Il Bohrbug si verifica quando:

- **Condizioni riproducibili**: Le condizioni che causano il bug sono sempre le stesse
- **Comportamento deterministico**: Il bug si manifesta sempre nello stesso modo
- **Nessuna interferenza**: Il processo di debugging non modifica il comportamento
- **Causa chiara**: La causa del bug è identificabile e costante

---

## Esempi comuni

### Esempio 1: Divisione per zero

```php
// Bug sempre riproducibile
public function calculateAverage($numbers) {
    $sum = array_sum($numbers);
    $count = count($numbers);
    return $sum / $count; // Bug: divisione per zero se $count è 0
}

// Ogni volta che chiami con array vuoto, ottieni lo stesso errore
calculateAverage([]); // Sempre: Division by zero
```

**Causa:** Il bug è deterministico e sempre riproducibile.

### Esempio 2: Null pointer

```php
// Bug sempre riproducibile
public function getUserName($userId) {
    $user = User::find($userId);
    return $user->name; // Bug: se $user è null, errore sempre
}

// Ogni volta che chiami con ID inesistente, stesso errore
getUserName(99999); // Sempre: Trying to get property of non-object
```

**Causa:** Il bug si manifesta sempre nelle stesse condizioni.

### Esempio 3: Errore di logica

```php
// Bug sempre riproducibile
public function isAdult($age) {
    return $age > 18; // Bug: dovrebbe essere >= 18
}

// Ogni volta con 18, stesso risultato sbagliato
isAdult(18); // Sempre: false (dovrebbe essere true)
```

**Causa:** La logica è sbagliata ma sempre la stessa.

---

## Come risolverlo

### 1. Identifica le condizioni

Poiché il bug è riproducibile, identifica esattamente le condizioni:

```php
// Test che riproduce sempre il bug
test('division by zero with empty array', function () {
    expect(calculateAverage([]))->toThrow(DivisionByZeroError::class);
});
```

### 2. Scrivi test che riproducono il bug

I Bohrbug sono perfetti per i test perché sono sempre riproducibili:

```php
test('null pointer with non-existent user', function () {
    expect(fn() => getUserName(99999))->toThrow(Error::class);
});
```

### 3. Fixa il bug

Una volta identificato, il fix è diretto:

```php
// Fix del bug
public function calculateAverage($numbers) {
    $sum = array_sum($numbers);
    $count = count($numbers);
    
    if ($count === 0) {
        return 0; // Gestisci il caso edge
    }
    
    return $sum / $count;
}
```

### 4. Verifica con test

I test dovrebbero passare dopo il fix:

```php
test('handles empty array', function () {
    expect(calculateAverage([]))->toBe(0);
});
```

---

## Prevenzione

- **Test edge cases**: Scrivi test per casi limite (array vuoti, null, zero)
- **Validazione input**: Valida sempre l'input prima di processarlo
- **Defensive programming**: Gestisci tutti i casi possibili
- **Code review**: Identifica potenziali Bohrbug durante la review

---

## Origine del termine

Il termine **Bohrbug** deriva dal modello atomico di **Niels Bohr** in fisica, dove gli elettroni seguono orbite prevedibili e deterministiche.

Il termine è stato coniato per descrivere bug che si comportano in modo simile: prevedibili, deterministici e sempre riproducibili, a differenza degli Heisenbug che cambiano comportamento quando osservati.

---

## Termini correlati

- **Heisenbug** - Bug che cambia comportamento quando osservato (opposto)
- **Schrödinbug** - Bug che non si manifesta finché non viene notato
- **Mandelbug** - Bug così complesso che sembra caotico

---

## Risorse utili

- [Wikipedia: Bohrbug](https://en.wikipedia.org/wiki/Heisenbug#Bohrbug)
- [Laravel Testing](https://laravel.com/docs/testing) - Guida ai test Laravel
- [PHPUnit Documentation](https://phpunit.de/documentation.html) - Framework di testing

