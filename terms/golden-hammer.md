# Golden Hammer

## Cosa significa

Il **Golden Hammer** (martello d'oro) è un anti-pattern dove una persona o team usa sempre lo stesso strumento, tecnologia o soluzione per ogni problema, indipendentemente dal fatto che sia appropriato. Deriva dal detto: "Quando hai un martello, tutto sembra un chiodo".

È quello che succede quando usi sempre Laravel per tutto, anche quando non serve, o sempre lo stesso pattern anche quando non è appropriato.

---

## Perché ti serve conoscerlo

Conoscere il termine "Golden Hammer" ti aiuta a:

- **Riconoscere quando usi sempre lo stesso strumento** anche quando non serve
- **Comunicare meglio** con il team: "Questo è golden hammer, valutiamo alternative"
- **Scegliere lo strumento giusto** per ogni problema
- **Evitare forzare soluzioni** che non si adattano

---

## Come funziona

Il Golden Hammer si verifica quando:

- **Stesso strumento sempre**: Usi sempre lo stesso strumento
- **Forzare soluzioni**: Forzi soluzioni che non si adattano
- **Comfort zone**: Resti nella tua comfort zone
- **Mancanza di alternative**: Non conosci alternative

---

## Esempi comuni

### Esempio 1: Laravel per tutto

```php
// Golden hammer: usi Laravel per tutto
// Anche per script CLI semplici che non ne hanno bisogno
// Anche per API micro che potrebbero essere più leggere
// Anche per progetti che non hanno bisogno di framework completo
```

**Problema:** Usi Laravel anche quando non serve.

### Esempio 2: Stesso pattern sempre

```php
// Golden hammer: usi sempre Repository pattern
// Anche quando Eloquent sarebbe sufficiente
// Anche quando non serve astrazione
// Anche quando complica inutilmente
```

**Problema:** Pattern usato anche quando non serve.

---

## Come evitarlo

### 1. Valuta alternative

Per ogni problema, valuta alternative:

```markdown
## Problema: API semplice
- Opzione 1: Laravel (completo ma pesante)
- Opzione 2: Lumen (leggero)
- Opzione 3: Slim (minimalista)
- Scelta: Valuta quale è più appropriato
```

### 2. Scegli strumento appropriato

Scegli lo strumento per il problema:

```php
// Problema semplice: script CLI
// Non serve Laravel completo
// Usa: script PHP semplice

// Problema complesso: applicazione web
// Serve framework completo
// Usa: Laravel
```

### 3. Esci dalla comfort zone

Impara nuovi strumenti:

```markdown
## Impara
- Framework diversi
- Pattern diversi
- Approcci diversi
```

---

## Prevenzione

- **Valuta alternative**: Valuta strumenti diversi
- **Scegli appropriato**: Scegli strumento per problema
- **Esci comfort zone**: Impara nuovi strumenti
- **Code review**: Identifica golden hammer durante review

---

## Origine del termine

Il termine **Golden Hammer** deriva dal detto: "When all you have is a hammer, everything looks like a nail" (Quando hai solo un martello, tutto sembra un chiodo).

---

## Termini correlati

- **Cargo Cult Programming** - Copiare senza capire
- **Not Invented Here** - Rifiutare soluzioni esistenti
- **Premature Optimization** - Ottimizzare troppo presto

---

## Risorse utili

- [Wikipedia: Golden Hammer](https://en.wikipedia.org/wiki/Law_of_the_instrument) - Articolo Wikipedia
- [Laravel Alternatives](https://laravel.com/docs) - Quando usare Laravel
