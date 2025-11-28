# Rubber Duck Debugging

## Cosa significa

Il **Rubber Duck Debugging** (debugging con papera di gomma) è una tecnica di debugging dove spieghi il problema a un oggetto inanimato (come una papera di gomma) per capirlo meglio. Il nome deriva dal libro "The Pragmatic Programmer" dove si suggerisce di spiegare il codice a una papera di gomma.

È quello che succede quando stai bloccato su un bug, inizi a spiegare il problema a qualcuno (o a te stesso), e durante la spiegazione capisci la soluzione.

---

## Perché ti serve conoscerlo

Conoscere il termine "Rubber Duck Debugging" ti aiuta a:

- **Risolvere bug più velocemente** spiegando il problema ad alta voce
- **Comunicare meglio** con il team: "Fammi fare rubber duck debugging" significa "fammi spiegare il problema"
- **Riconoscere quando sei bloccato** e hai bisogno di cambiare approccio
- **Migliorare la comprensione** del codice attraverso la spiegazione

---

## Come funziona

Il Rubber Duck Debugging funziona perché:

- **Spiegare forza la chiarezza**: Devi organizzare i pensieri per spiegare
- **Rivelazione durante la spiegazione**: Spesso capisci il problema mentre lo spieghi
- **Cambio di prospettiva**: Spiegare ti fa vedere il problema da un'altra angolazione
- **Identificazione di assunzioni**: Spiegando, noti assunzioni sbagliate

---

## Esempi comuni

### Esempio 1: Spiegare a te stesso

```php
// Sei bloccato su questo bug:

public function processOrder($orderId) {
    $order = Order::find($orderId);
    $total = $order->items->sum('price');
    return $total;
}

// Inizi a spiegare a te stesso:
// "Ok, prendo l'ordine, poi sommo i prezzi degli item...
// Aspetta, ma se l'ordine non esiste? E se items è vuoto?
// Ah! Il problema è che non gestisco il caso in cui Order::find() ritorna null!"
```

**Risultato:** Durante la spiegazione hai capito il problema.

### Esempio 2: Spiegare a un collega

```javascript
// Sei bloccato:

function calculateDiscount(price, discount) {
    return price - (price * discount);
}

// Spieghi al collega:
// "Devo calcolare lo sconto, prendo il prezzo, moltiplico per lo sconto...
// Aspetta, lo sconto è in percentuale o decimale? Se è 20%, devo fare price * 0.20!
// Ah! Il problema è che lo sconto viene passato come 20 invece di 0.20!"
```

**Risultato:** Spiegando hai identificato il problema di unità.

### Esempio 3: Spiegare a una papera (o oggetto)

```php
// Sei bloccato:

public function validateEmail($email) {
    return filter_var($email, FILTER_VALIDATE_EMAIL);
}

// Spieghi alla papera:
// "Devo validare l'email, uso filter_var...
// Ma aspetta, filter_var ritorna false se non valida, ma cosa ritorna se valida?
// Ah! Ritorna l'email stessa! Quindi devo controllare !== false, non == true!"
```

**Risultato:** Spiegando hai capito il comportamento della funzione.

---

## Come applicarlo

### 1. Spiega il problema ad alta voce

Anche se sei solo, spiega il problema ad alta voce:

```
"Ok, il problema è che quando faccio X, succede Y invece di Z.
Prima di tutto, X fa questo... poi dovrebbe fare... ma invece..."
```

### 2. Spiega passo per passo

Spiega ogni passo del codice come se l'ascoltatore non sapesse nulla:

```php
// Invece di pensare:
// "Questa funzione non funziona"

// Spiega:
// "Questa funzione prende un ID, cerca l'utente nel database,
// poi calcola il totale degli ordini, poi applica lo sconto...
// Aspetta, ma lo sconto viene applicato prima o dopo il calcolo del totale?"
```

### 3. Usa un oggetto fisico

Avere un oggetto fisico (papera, peluche, statuetta) aiuta:

- Ti ricorda di spiegare
- Ti costringe a verbalizzare
- Cambia la prospettiva mentale

### 4. Scrivi la spiegazione

A volte scrivere la spiegazione è più efficace:

```markdown
## Problema
La funzione non ritorna il valore corretto.

## Cosa dovrebbe fare
1. Prendere l'input
2. Validarlo
3. Processarlo
4. Ritornare il risultato

## Cosa fa invece
1. Prendere l'input
2. Validarlo
3. [Qui si ferma?]
4. Non ritorna nulla

## Ah! Il problema è che la validazione fallisce silenziosamente!
```

### 5. Spiega a un collega

Spiegare a un collega è ancora più efficace:

- Ti costringe a essere chiaro
- Il collega può fare domande
- Il collega può notare cose che tu non vedi

---

## Quando usarlo

Usa Rubber Duck Debugging quando:

- **Sei bloccato** su un bug da più di 30 minuti
- **Il codice sembra corretto** ma non funziona
- **Non capisci** perché qualcosa non funziona
- **Hai provato tutto** ma niente funziona
- **Hai bisogno** di cambiare prospettiva

---

## Origine del termine

Il termine **Rubber Duck Debugging** deriva dal libro **"The Pragmatic Programmer"** di Andrew Hunt e David Thomas (1999).

Nel libro, si racconta la storia di un programmatore che porta una papera di gomma e le spiega il codice, riga per riga, per trovare bug.

Il termine è diventato popolare nella comunità di sviluppo come tecnica efficace per il debugging.

---

## Termini correlati

- **Rubber Ducking** - Variante del termine
- **Pair Programming** - Debugging con un partner
- **Code Review** - Spiegare il codice ad altri

---

## Risorse utili

- [The Pragmatic Programmer](https://pragprog.com/titles/tpp20/the-pragmatic-programmer-20th-anniversary-edition/) - Libro originale
- [Wikipedia: Rubber Duck Debugging](https://en.wikipedia.org/wiki/Rubber_duck_debugging)
- [Laravel Debugging](https://laravel.com/docs/errors) - Strumenti di debugging Laravel

