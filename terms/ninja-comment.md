# Ninja Comment

## Cosa significa

Il **Ninja Comment** (commento ninja) è un commento nel codice che spiega perché qualcosa non funziona o perché è stato fatto in un modo strano, invece di fixare il problema. Il nome deriva dal fatto che questi commenti "appare" come un ninja quando meno te lo aspetti.

È quello che succede quando invece di fixare un bug, aggiungi un commento che spiega perché non funziona: "// TODO: questo non funziona ma non so perché"

---

## Perché ti serve conoscerlo

Conoscere il termine "Ninja Comment" ti aiuta a:

- **Riconoscere commenti che nascondono problemi** invece di risolverli
- **Comunicare meglio** con il team: "Questo è un ninja comment, dovremmo fixare il problema"
- **Identificare quando fixare** invece di commentare
- **Migliorare la qualità** del codice risolvendo problemi invece di commentarli

---

## Come funziona

Il Ninja Comment si verifica quando:

- **Commenti che spiegano bug**: Commenti che spiegano perché qualcosa non funziona
- **TODO infiniti**: Commenti TODO che non vengono mai risolti
- **Workaround documentati**: Commenti che documentano workaround invece di fix
- **Scuse nel codice**: Commenti che giustificano codice problematico

---

## Esempi comuni

### Esempio 1: Commento che spiega un bug

```php
// Ninja comment: spiega perché non funziona invece di fixare
public function calculateTotal($items) {
    // TODO: Questo non funziona con array vuoti, ma non so perché
    // FIXME: A volte ritorna null invece di 0
    return array_sum(array_column($items, 'price'));
}
```

**Problema:** Il commento documenta il bug invece di fixarlo.

### Esempio 2: Workaround documentato

```php
// Ninja comment: documenta workaround invece di fix
public function processOrder($order) {
    // HACK: Devo fare questo perché la funzione originale ha un bug
    // che non abbiamo tempo di fixare. Funziona ma è un workaround.
    $total = $this->calculateTotalHack($order->items);
    
    // WORKAROUND: La funzione save() a volte fallisce silenziosamente
    // quindi devo controllare manualmente
    if (!$order->save()) {
        Log::error('Save failed');
    }
}
```

**Problema:** Workaround documentati invece di fix.

### Esempio 3: Scuse nel codice

```php
// Ninja comment: giustifica codice problematico
public function getUser($id) {
    // SORRY: Questo codice è un po' complesso ma funziona
    // Non ho avuto tempo di refactorare, ma prometto che lo farò
    // (scritto 2 anni fa e mai refactorato)
    
    // Codice complesso qui
}
```

**Problema:** Commenti che giustificano invece di migliorare.

---

## Come risolverlo

### 1. Fixa invece di commentare

Se c'è un problema, fixalo invece di commentarlo:

```php
// Prima: ninja comment
// TODO: Non funziona con array vuoti
return array_sum(array_column($items, 'price'));

// Dopo: fix
if (empty($items)) {
    return 0;
}
return array_sum(array_column($items, 'price'));
```

### 2. Crea issue invece di TODO

Se non puoi fixare subito, crea un'issue:

```php
// Prima: TODO infinito
// TODO: Fixare questo bug

// Dopo: riferimento a issue
// See issue #123 for details
```

### 3. Rimuovi commenti obsoleti

Rimuovi commenti che non sono più validi:

```php
// Rimuovi commenti vecchi che non sono più rilevanti
```

### 4. Documenta il perché, non il cosa

Commenta il perché, non il cosa:

```php
// Prima: ninja comment
// Questo non funziona

// Dopo: commento utile
// Usa cache perché la query è lenta (vedi issue #456)
```

---

## Prevenzione

- **Fix immediato**: Fixa problemi invece di commentarli
- **Issue tracking**: Crea issue per problemi che non puoi fixare subito
- **Code review**: Identifica ninja comment durante le review
- **Refactoring**: Rimuovi commenti obsoleti durante il refactoring

---

## Origine del termine

Il termine **Ninja Comment** deriva dall'analogia con i ninja: così come i ninja appaiono quando meno te lo aspetti, i ninja comment appaiono nel codice quando meno te lo aspetti, rivelando problemi nascosti.

---

## Termini correlati

- **Code Smell** - Indicatore di problemi nel codice
- **Technical Debt** - Debito tecnico accumulato
- **Dead Code** - Codice che non serve più

---

## Risorse utili

- [Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882) - Libro su codice pulito
- [Laravel Best Practices](https://laravel.com/docs) - Best practices Laravel
