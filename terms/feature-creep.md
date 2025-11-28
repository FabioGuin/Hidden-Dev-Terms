# Feature Creep

## Cosa significa

Il **Feature Creep** (strisciamento delle funzionalità) è il fenomeno per cui un progetto accumula continuamente nuove funzionalità oltre lo scope originale, rendendolo più complesso e difficile da completare.

È quello che succede quando aggiungi funzionalità "tanto ci siamo" durante lo sviluppo, allontanandoti dall'obiettivo originale.

---

## Perché ti serve conoscerlo

Conoscere il termine "Feature Creep" ti aiuta a:

- **Riconoscere quando aggiungi funzionalità non necessarie**
- **Comunicare meglio** con il team: "Questo è feature creep, rimaniamo focalizzati"
- **Mantenere lo scope** del progetto sotto controllo
- **Evitare complessità** inutile

---

## Come funziona

Il Feature Creep si verifica quando:

- **"Tanto ci siamo"**: Aggiungi funzionalità perché "tanto ci siamo"
- **Scope drift**: Lo scope del progetto si allarga continuamente
- **Mancanza di focus**: Non ti concentri sull'obiettivo originale
- **Richiesta continua**: Aggiungi funzionalità su richiesta continua

---

## Esempi comuni

### Esempio 1: "Tanto ci siamo"

```php
// Feature creep: aggiungi funzionalità "tanto ci siamo"
// Obiettivo originale: sistema di login
// Aggiungi: "tanto ci siamo, aggiungiamo anche social login"
// Aggiungi: "tanto ci siamo, aggiungiamo anche 2FA"
// Aggiungi: "tanto ci siamo, aggiungiamo anche password reset"
// Risultato: progetto molto più complesso del previsto
```

**Problema:** Aggiungi funzionalità non nello scope originale.

### Esempio 2: Scope drift

```markdown
## Scope Originale
- Sistema di ordini base

## Dopo Feature Creep
- Sistema di ordini
- Sistema di pagamenti
- Sistema di notifiche
- Dashboard analytics
- Report avanzati
- Integrazione con ERP
```

**Problema:** Lo scope si allarga continuamente.

---

## Come evitarlo

### 1. Mantieni lo scope

Focalizzati sull'obiettivo originale:

```markdown
## Scope Originale
- [ ] Feature 1
- [ ] Feature 2
- [ ] Feature 3

## Non nello scope (per ora)
- [ ] Feature 4 (per versione 2)
- [ ] Feature 5 (per versione 2)
```

### 2. Usa backlog

Metti nuove funzionalità nel backlog:

```markdown
## Backlog
- Feature 4 (dopo MVP)
- Feature 5 (dopo MVP)
```

### 3. Chiedi "Perché?"

Per ogni nuova funzionalità, chiedi "Perché?"

```
"Perché aggiungiamo questa funzionalità?"
"È nello scope originale?"
"Possiamo farlo dopo?"
```

### 4. MVP First

Completa MVP prima di aggiungere funzionalità:

```markdown
## MVP (Minimum Viable Product)
- [ ] Feature essenziale 1
- [ ] Feature essenziale 2

## Dopo MVP
- [ ] Feature aggiuntiva 1
- [ ] Feature aggiuntiva 2
```

---

## Prevenzione

- **Scope chiaro**: Definisci scope chiaro all'inizio
- **Backlog**: Metti nuove funzionalità nel backlog
- **Chiedi "Perché?"**: Valuta ogni nuova funzionalità
- **MVP First**: Completa MVP prima di aggiungere

---

## Origine del termine

Il termine **Feature Creep** deriva dalla gestione progetti e descrive come le funzionalità "strisciano" nel progetto oltre lo scope originale.

---

## Termini correlati

- **Scope Creep** - Allargamento dello scope
- **YAGNI** - You Aren't Gonna Need It
- **MVP** - Minimum Viable Product

---

## Risorse utili

- [Wikipedia: Feature Creep](https://en.wikipedia.org/wiki/Feature_creep) - Articolo Wikipedia
- [Laravel Best Practices](https://laravel.com/docs) - Best practices
