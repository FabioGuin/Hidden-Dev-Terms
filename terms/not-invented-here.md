# Not Invented Here (NIH) Syndrome

## Cosa significa

Il **Not Invented Here (NIH) Syndrome** (sindrome "non inventato qui") è la tendenza a rifiutare soluzioni, librerie o codice esistenti e preferire scrivere tutto da zero, anche quando esistono soluzioni mature e testate.

È l'opposto del Cargo Cult Programming: invece di copiare senza capire, rifiuti tutto ciò che non hai scritto tu.

---

## Perché ti serve conoscerlo

Conoscere il termine "NIH Syndrome" ti aiuta a:

- **Riconoscere quando rifiuti soluzioni esistenti** senza motivo
- **Comunicare meglio** con il team: "Questo è NIH syndrome, usiamo librerie esistenti"
- **Valutare soluzioni esistenti** invece di riscrivere tutto
- **Risparmiare tempo** usando soluzioni mature

---

## Come funziona

Il NIH Syndrome si verifica quando:

- **Rifiuti librerie**: Rifiuti librerie esistenti
- **Riscrivi tutto**: Preferisci riscrivere invece di usare
- **Non ti fidi**: Non ti fidi di codice che non hai scritto
- **Reinventi la ruota**: Riscrivi cose già esistenti

---

## Esempi comuni

### Esempio 1: Riscrivi invece di usare

```php
// NIH syndrome: riscrivi invece di usare libreria
// Invece di: usare Guzzle per HTTP
// Riscrivi: tua implementazione HTTP da zero

class MyHttpClient {
    // Riscrivi tutto invece di usare Guzzle
    // Anche se Guzzle è maturo, testato, e mantenuto
}
```

**Problema:** Riscrivi invece di usare soluzioni esistenti.

### Esempio 2: Non ti fidi di codice esterno

```php
// NIH syndrome: non ti fidi di codice esterno
// "Non so come funziona, meglio riscriverlo"
// "Non mi fido di questa libreria"
// "Preferisco controllare tutto io"
```

**Problema:** Rifiuti soluzioni senza motivo valido.

---

## Come evitarlo

### 1. Valuta soluzioni esistenti

Prima di riscrivere, valuta soluzioni esistenti:

```markdown
## Problema: HTTP Client
- Opzione 1: Usa Guzzle (maturo, testato)
- Opzione 2: Riscrivi da zero (tempo, bug, manutenzione)
- Scelta: Valuta pro e contro
```

### 2. Usa librerie mature

Usa librerie mature e mantenute:

```php
// Invece di: riscrivere
// Usa: libreria matura
use GuzzleHttp\Client;

$client = new Client();
```

### 3. Contribuisci invece di riscrivere

Se una libreria non fa quello che vuoi:

```markdown
## Opzioni
1. Contribuisci alla libreria esistente
2. Estendi la libreria esistente
3. Usa libreria esistente + wrapper
4. Riscrivi solo se necessario
```

---

## Prevenzione

- **Valuta esistenti**: Valuta soluzioni esistenti prima
- **Usa mature**: Usa librerie mature e mantenute
- **Contribuisci**: Contribuisci invece di riscrivere
- **Riscrivi solo se necessario**: Riscrivi solo se davvero necessario

---

## Origine del termine

Il termine **Not Invented Here (NIH) Syndrome** deriva dalla cultura aziendale dove si preferisce sviluppare internamente invece di usare soluzioni esterne.

---

## Termini correlati

- **Cargo Cult Programming** - Copiare senza capire (opposto)
- **Golden Hammer** - Usare sempre stesso strumento
- **Reinventing the Wheel** - Riscrivere cose esistenti

---

## Risorse utili

- [Wikipedia: Not Invented Here](https://en.wikipedia.org/wiki/Not_invented_here) - Articolo Wikipedia
- [Laravel Packages](https://packagist.org/) - Librerie PHP
- [Composer](https://getcomposer.org/) - Gestione dipendenze
