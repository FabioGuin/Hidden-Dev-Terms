# Yak Shaving

## Cosa significa

Lo **Yak Shaving** è il fenomeno per cui devi completare una serie apparentemente infinita di task irrilevanti per raggiungere un obiettivo originale. Il nome deriva da una storia dove per comprare una spazzola per il cane, devi prima tosare uno yak.

È quello che succede quando inizi con un obiettivo semplice, ma ti ritrovi a fare una catena di task sempre più lontani dall'obiettivo originale.

---

## Perché ti serve conoscerlo

Conoscere il termine "Yak Shaving" ti aiuta a:

- **Riconoscere quando stai perdendo il focus** su task irrilevanti
- **Valutare se un task è necessario** o è solo yak shaving
- **Comunicare meglio** con il team: "Stiamo facendo yak shaving, torniamo all'obiettivo originale"
- **Pianificare meglio** identificando dipendenze reali vs apparenti

---

## Come funziona

Lo Yak Shaving si verifica quando:

- **Dipendenze a catena**: Ogni task richiede un altro task prima di essere completato
- **Perfezionismo**: Vuoi che tutto sia perfetto prima di procedere
- **Distrazione**: Ti perdi in dettagli che sembrano importanti ma non lo sono
- **Mancanza di priorità**: Non distingui tra task necessari e opzionali

---

## Esempi comuni

### Esempio 1: Fix di un bug

```
Obiettivo originale: Fixare un bug nel login

1. Devo aggiornare le dipendenze per testare
2. Le dipendenze richiedono PHP 8.2
3. Devo aggiornare il server
4. Il server richiede un aggiornamento del sistema operativo
5. Devo aggiornare Docker
6. Docker richiede un aggiornamento di macOS
7. macOS richiede un backup completo
8. ...

Risultato: Non hai ancora fixato il bug
```

**Problema:** Hai perso di vista l'obiettivo originale.

### Esempio 2: Setup ambiente

```
Obiettivo originale: Testare una nuova feature

1. Devo aggiornare Laravel
2. Laravel richiede PHP 8.2
3. Devo aggiornare Composer
4. Composer richiede aggiornamento di Homebrew
5. Homebrew richiede aggiornamento di Xcode
6. Xcode richiede aggiornamento di macOS
7. ...

Risultato: Non hai ancora testato la feature
```

**Problema:** Potresti testare la feature senza tutti questi aggiornamenti.

### Esempio 3: Refactoring

```
Obiettivo originale: Aggiungere una nuova funzione

1. Devo prima refactorare questa classe
2. Il refactoring richiede di aggiornare i test
3. I test richiedono di aggiornare il framework di test
4. Il framework richiede di aggiornare PHPUnit
5. PHPUnit richiede di aggiornare PHP
6. ...

Risultato: Non hai ancora aggiunto la funzione
```

**Problema:** Potresti aggiungere la funzione senza tutto questo refactoring.

---

## Come evitarlo

### 1. Identifica l'obiettivo originale

Chiediti sempre: "Qual è il mio obiettivo originale?"

```markdown
Obiettivo: Fixare bug nel login
Task necessari: 
- [ ] Trovare la causa del bug
- [ ] Scrivere fix
- [ ] Testare fix

Task NON necessari:
- [ ] Aggiornare tutto l'ambiente
- [ ] Refactorare tutto il codice
- [ ] Migliorare altri aspetti
```

### 2. Valuta se il task è necessario

Per ogni task, chiediti: "Questo è davvero necessario per l'obiettivo?"

```php
// Obiettivo: Aggiungere validazione email

// Yak Shaving:
// - Refactorare tutta la classe User
// - Migliorare tutti i test
// - Aggiornare documentazione completa

// Necessario:
// - Aggiungere regola di validazione
// - Test per la nuova validazione
```

### 3. Usa workaround temporanei

A volte un workaround è meglio di una soluzione perfetta:

```php
// Obiettivo: Testare una feature

// Yak Shaving:
// Aggiornare tutto l'ambiente per supportare PHP 8.2

// Workaround:
// Usare ambiente esistente, testare la logica senza aggiornamenti
```

### 4. Time-boxing

Limita il tempo per task che potrebbero essere yak shaving:

```
"Spendo massimo 30 minuti su questo setup, poi torno all'obiettivo"
```

### 5. Documenta le dipendenze

Traccia le dipendenze reali vs apparenti:

```markdown
## Dipendenze Reali
- Feature richiede Laravel 10 (necessario)

## Dipendenze Apparenti (Yak Shaving)
- Aggiornare tutto il progetto a Laravel 11 (non necessario ora)
```

---

## Quando è accettabile

Non tutto lo yak shaving è negativo:

- **Manutenzione preventiva**: A volte è meglio aggiornare prima che diventi un problema
- **Debito tecnico**: Se stai pagando debito tecnico, è accettabile
- **Pianificazione**: Se hai pianificato questi task, non è yak shaving

Il problema è quando diventa una scusa per evitare il lavoro reale.

---

## Origine del termine

Il termine **Yak Shaving** deriva da una storia ricorsiva:

> "Vuoi comprare una spazzola per il cane. Per comprare la spazzola, devi andare al negozio. Per andare al negozio, devi tosare lo yak. Per tosare lo yak, devi..."

La storia continua con task sempre più lontani dall'obiettivo originale.

Il termine è diventato popolare nella comunità di sviluppo per descrivere questa catena infinita di dipendenze.

---

## Termini correlati

- **Bikeshedding** - Perdere tempo su decisioni banali
- **Analysis Paralysis** - Paralisi da troppa analisi
- **Gold Plating** - Aggiungere funzionalità non richieste

---

## Risorse utili

- [Wikipedia: Yak Shaving](https://en.wikipedia.org/wiki/Yak_shaving)
- [The Yak Shaving Blog](https://sethgodin.typepad.com/seths_blog/2005/03/dont_shave_that.html) - Articolo originale
- [Laravel: Keep It Simple](https://laravel.com/docs) - Focus sulla semplicità

