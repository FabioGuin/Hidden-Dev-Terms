# Dead Code

## Cosa significa

Il **Dead Code** (codice morto) è codice che non viene mai eseguito ma è ancora presente nel progetto. Può essere codice commentato, funzioni mai chiamate, o branch di codice inaccessibili.

È quello che succede quando hai codice che non serve più ma è ancora lì, occupando spazio e creando confusione.

---

## Perché ti serve conoscerlo

Conoscere il termine "Dead Code" ti aiuta a:

- **Riconoscere codice inutilizzato** che può essere rimosso
- **Comunicare meglio** con il team: "Questo è dead code, possiamo rimuoverlo"
- **Pulire il codice** rimuovendo parti non necessarie
- **Ridurre la complessità** eliminando codice che non serve

---

## Come funziona

Il Dead Code si verifica quando:

- **Codice commentato**: Codice commentato che non viene mai usato
- **Funzioni mai chiamate**: Funzioni definite ma mai invocate
- **Branch inaccessibili**: Codice in if/else che non può essere raggiunto
- **Import non usati**: Import di librerie mai utilizzate
- **Variabili non usate**: Variabili definite ma mai lette

---

## Esempi comuni

### Esempio 1: Codice commentato

```php
// Dead code: codice commentato mai usato
public function processOrder($order) {
    // $oldTotal = $order->total;
    // $order->total = $oldTotal * 1.1;
    // Questo codice non viene mai eseguito
    
    $order->total = calculateNewTotal($order);
}
```

**Problema:** Codice commentato che non serve più.

### Esempio 2: Funzione mai chiamata

```php
// Dead code: funzione definita ma mai chiamata
public function oldCalculateTotal($items) {
    // Logica vecchia mai usata
    $total = 0;
    foreach ($items as $item) {
        $total += $item->price;
    }
    return $total;
}

// Funzione nuova usata invece
public function calculateTotal($items) {
    return array_sum(array_column($items, 'price'));
}
```

**Problema:** Funzione vecchia mai chiamata.

### Esempio 3: Branch inaccessibile

```php
// Dead code: branch che non può essere raggiunto
public function process($data) {
    if ($data === null) {
        return null;
    }
    
    // Questo codice è dead code se $data non può essere null
    if ($data === null) {
        throw new Exception('Data is null');
    }
}
```

**Problema:** Codice che non può essere eseguito.

---

## Come risolverlo

### 1. Rimuovi codice commentato

Se il codice è commentato e non serve, rimuovilo:

```php
// Prima: codice commentato
// $oldTotal = $order->total;

// Dopo: rimosso
$order->total = calculateNewTotal($order);
```

### 2. Rimuovi funzioni non usate

Se una funzione non è mai chiamata, rimuovila:

```php
// Rimuovi funzioni mai chiamate
// Usa strumenti di static analysis per trovarle
```

### 3. Usa strumenti di analisi

Usa strumenti per trovare dead code:

```bash
# PHPStan rileva dead code
vendor/bin/phpstan analyse --level max

# Psalm rileva dead code
vendor/bin/psalm
```

### 4. Version control

Se hai dubbi, usa git per tracciare:

```bash
# Se rimuovi codice, git lo traccia
git commit -m "Remove dead code"
```

---

## Prevenzione

- **Static analysis**: Usa strumenti che rilevano dead code
- **Code review**: Identifica dead code durante le review
- **Refactoring**: Rimuovi codice non necessario durante il refactoring
- **Test**: I test rivelano codice non testato (potenzialmente dead)

---

## Origine del termine

Il termine **Dead Code** è stato coniato nella programmazione per descrivere codice che non viene mai eseguito.

L'analogia con la morte è efficace: così come un corpo morto non funziona più, dead code non viene eseguito più.

---

## Termini correlati

- **Zombie Code** - Codice che dovrebbe essere morto ma continua a essere eseguito
- **Code Smell** - Indicatore di problemi nel codice
- **Refactoring** - Processo di miglioramento del codice

---

## Risorse utili

- [PHPStan](https://phpstan.org/) - Static analysis per PHP
- [Psalm](https://psalm.dev/) - Static analysis per PHP
- [Laravel Best Practices](https://laravel.com/docs) - Best practices Laravel
