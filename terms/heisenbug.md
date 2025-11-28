# Heisenbug

## Cosa significa

Il **Heisenbug** è un bug che scompare o cambia comportamento quando cerchi di debuggarlo o osservarlo. Il nome deriva dal principio di indeterminazione di Heisenberg in fisica quantistica, secondo cui l'osservazione di un fenomeno ne modifica il comportamento.

È quello che succede quando un bug funziona perfettamente in produzione ma fallisce quando provi a riprodurlo in locale, o quando aggiungi un `console.log` e il bug magicamente scompare.

---

## Perché ti serve conoscerlo

Conoscere il termine "Heisenbug" ti aiuta a:

- **Comunicare meglio** con il team: invece di dire "il bug scompare quando lo debugg", puoi dire "abbiamo un Heisenbug"
- **Riconoscere il problema** più velocemente: quando un bug si comporta in modo strano durante il debug, sai che è un Heisenbug
- **Cercare soluzioni** specifiche: sapere il nome ti permette di trovare tecniche e pattern per gestire questo tipo di bug

---

## Come funziona

Il Heisenbug si verifica quando il processo di debugging modifica le condizioni che causano il bug:

- **Timing**: Aggiungere breakpoint o log cambia i tempi di esecuzione
- **Memoria**: Il debugger può modificare l'allocazione della memoria
- **Stato**: Aggiungere codice di debug può inizializzare variabili o cambiare lo stato
- **Ambiente**: Differenze tra ambiente di produzione e sviluppo

---

## Esempi comuni

### Esempio 1: Bug che scompare con console.log

```javascript
// Bug: la funzione non funziona
function processData(data) {
    let result = data.map(item => item.value);
    return result;
}

// Aggiungi un console.log per debug...
function processData(data) {
    console.log(data); // <-- Questo fa funzionare il codice!
    let result = data.map(item => item.value);
    return result;
}
```

**Causa:** Il `console.log` può cambiare il timing o inizializzare variabili che risolvono il problema.

### Esempio 2: Bug che funziona solo in produzione

```php
// In produzione funziona
$user = User::find($id);

// In locale con debug attivo fallisce
if (config('app.debug')) {
    // Codice di debug che modifica lo stato
}
$user = User::find($id); // <-- Fallisce qui
```

**Causa:** Il codice di debug modifica lo stato dell'applicazione o del database.

### Esempio 3: Race condition

```javascript
// Bug intermittente che scompare quando aggiungi un delay
async function fetchData() {
    const data1 = await api.get('/endpoint1');
    const data2 = await api.get('/endpoint2');
    return combine(data1, data2);
}

// Aggiungi un log e funziona...
async function fetchData() {
    const data1 = await api.get('/endpoint1');
    console.log('Got data1'); // <-- Cambia il timing
    const data2 = await api.get('/endpoint2');
    return combine(data1, data2);
}
```

**Causa:** Il `console.log` introduce un delay che risolve la race condition.

---

## Come risolverlo

### 1. Usa logging non invasivo

Invece di `console.log`, usa logging strutturato che non modifica il timing:

```php
// Laravel
Log::debug('Processing data', ['data' => $data]);
```

### 2. Debug remoto

Usa strumenti di debug remoto che non modificano l'ambiente:

- **Laravel Telescope** per debugging in produzione
- **Sentry** per error tracking
- **Xdebug** con configurazione remota

### 3. Reproduzione controllata

Crea test che riproducono esattamente le condizioni di produzione:

```php
// Test che replica l'ambiente di produzione
test('reproduce heisenbug', function () {
    config(['app.debug' => false]);
    // Test senza modifiche al timing
});
```

### 4. Isolamento del problema

Riduci il codice al minimo necessario per riprodurre il bug:

```php
// Rimuovi tutto il codice non essenziale
// Aggiungi solo quello necessario per il bug
```

---

## Prevenzione

- **Test in ambiente simile alla produzione**: Usa ambienti di staging identici alla produzione
- **Logging strutturato**: Usa logging che non modifica il comportamento
- **Code review**: Identifica potenziali race condition o problemi di timing
- **Monitoring**: Usa strumenti di monitoring che non interferiscono con l'esecuzione

---

## Origine del termine

Il termine **Heisenbug** deriva dal principio di indeterminazione di **Werner Heisenberg** in fisica quantistica, che afferma che l'osservazione di un fenomeno ne modifica il comportamento.

Il termine è stato coniato nella comunità di sviluppo per descrivere bug che si comportano in modo simile: quando cerchi di osservarli (debug), cambiano comportamento o scompaiono.

---

## Termini correlati

- **Schrödinbug** - Bug che non si manifesta finché qualcuno non lo nota
- **Bohrbug** - Bug che si comporta sempre nello stesso modo (opposto di Heisenbug)
- **Mandelbug** - Bug così complesso che il suo comportamento sembra caotico

---

## Risorse utili

- [Wikipedia: Heisenbug](https://en.wikipedia.org/wiki/Heisenbug)
- [The Debugging Book](https://www.debuggingbook.org/) - Guida completa al debugging
- [Laravel Telescope](https://laravel.com/docs/telescope) - Debugging tool per Laravel

