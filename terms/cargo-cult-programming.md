# Cargo Cult Programming

## Cosa significa

Il **Cargo Cult Programming** (programmazione cargo cult) è la pratica di copiare codice o pattern senza capire perché funzionano. Il nome deriva dai "cargo cult" del Pacifico che imitavano rituali senza capirne il significato.

È quello che succede quando copi codice da Stack Overflow senza capire perché funziona, o usi pattern senza sapere quando servono.

---

## Perché ti serve conoscerlo

Conoscere il termine "Cargo Cult Programming" ti aiuta a:

- **Riconoscere quando copi senza capire** codice o pattern
- **Comunicare meglio** con il team: "Questo è cargo cult programming, capiamo perché funziona"
- **Imparare invece di copiare** codice e pattern
- **Usare pattern consapevolmente** invece di imitarli

---

## Come funziona

Il Cargo Cult Programming si verifica quando:

- **Copia senza capire**: Copi codice senza capire perché funziona
- **Pattern senza contesto**: Usi pattern senza sapere quando servono
- **Imitazione**: Imiti codice senza capire il problema che risolve
- **Magia**: Tratti il codice come "magia" invece di capirlo

---

## Esempi comuni

### Esempio 1: Copia da Stack Overflow

```php
// Cargo cult: copiato da Stack Overflow senza capire
public function process($data) {
    // Non so perché serve questo, ma funziona
    $data = array_map('trim', $data);
    $data = array_filter($data);
    $data = array_values($data);
    return $data;
}

// Problema: non capisci perché ogni passaggio serve
```

**Problema:** Copiato senza capire il perché.

### Esempio 2: Pattern senza contesto

```php
// Cargo cult: usi pattern senza sapere perché
class OrderService {
    // Uso Repository pattern perché l'ho visto in un tutorial
    // Ma non so se serve qui
    public function __construct(OrderRepository $repository) {
        $this->repository = $repository;
    }
}

// Problema: pattern usato senza capire se serve
```

**Problema:** Pattern usato senza capire il contesto.

---

## Come evitarlo

### 1. Capisci prima di copiare

Prima di copiare, capisci:

```php
// Prima: copia
// Dopo: capisci
// array_map('trim', $data) - rimuove spazi da ogni elemento
// array_filter($data) - rimuove elementi vuoti
// array_values($data) - reindirizza array
```

### 2. Leggi documentazione

Leggi documentazione invece di copiare:

```php
// Invece di: copiare da Stack Overflow
// Leggi: documentazione ufficiale
// Capisci: perché funziona
```

### 3. Chiedi "Perché?"

Per ogni pattern, chiedi "Perché?"

```
"Perché uso questo pattern?"
"Quale problema risolve?"
"È necessario qui?"
```

---

## Prevenzione

- **Capisci prima di copiare**: Capisci codice prima di copiare
- **Leggi documentazione**: Leggi documentazione ufficiale
- **Chiedi "Perché?"**: Valuta ogni pattern
- **Impara**: Impara invece di imitare

---

## Origine del termine

Il termine **Cargo Cult Programming** deriva dai "cargo cult" del Pacifico che imitavano rituali (come costruire piste di atterraggio) senza capirne il significato, sperando che aerei con cargo arrivassero.

---

## Termini correlati

- **Golden Hammer** - Usare sempre lo stesso strumento
- **Not Invented Here** - Rifiutare soluzioni esistenti
- **Code Smell** - Indicatore di problemi

---

## Risorse utili

- [Wikipedia: Cargo Cult Programming](https://en.wikipedia.org/wiki/Cargo_cult_programming) - Articolo Wikipedia
- [Laravel Documentation](https://laravel.com/docs) - Documentazione ufficiale
