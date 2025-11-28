# Scope Creep

## Cosa significa

Lo **Scope Creep** (strisciamento dello scope) è il fenomeno per cui lo scope di un progetto si allarga continuamente oltre i requisiti originali, rendendo il progetto più complesso e difficile da completare.

È simile al Feature Creep ma si riferisce specificamente all'allargamento dello scope del progetto.

---

## Perché ti serve conoscerlo

Conoscere il termine "Scope Creep" ti aiuta a:

- **Riconoscere quando lo scope si allarga** oltre i requisiti
- **Comunicare meglio** con il team: "Questo è scope creep, rimaniamo focalizzati"
- **Mantenere lo scope** del progetto sotto controllo
- **Gestire le richieste** del cliente in modo controllato

---

## Come funziona

Lo Scope Creep si verifica quando:

- **Requisiti che cambiano**: I requisiti cambiano continuamente
- **Richiesta continua**: Il cliente chiede continuamente nuove funzionalità
- **Mancanza di controllo**: Non controlli lo scope del progetto
- **"Piccole" aggiunte**: Aggiungi "piccole" cose che si accumulano

---

## Esempi comuni

### Esempio 1: Requisiti che cambiano

```
Progetto originale: Sistema di ordini base
+ "Aggiungiamo anche gestione inventario"
+ "Aggiungiamo anche sistema di pagamenti"
+ "Aggiungiamo anche dashboard"
+ "Aggiungiamo anche report"
Risultato: progetto completamente diverso
```

**Problema:** Lo scope si allarga continuamente.

---

## Come evitarlo

### 1. Definisci scope chiaro

Documenta lo scope all'inizio:

```markdown
## Scope del Progetto
- Sistema di ordini base
- Gestione prodotti
- Sistema di autenticazione

## Fuori dallo scope
- Sistema di pagamenti (fase 2)
- Dashboard analytics (fase 2)
```

### 2. Gestisci cambiamenti

Gestisci cambiamenti come modifiche formali:

```markdown
## Change Request
- Richiesta: Aggiungere sistema di pagamenti
- Impatto: +2 settimane
- Approvazione: [ ] Sì [ ] No
```

### 3. Dì "No" quando necessario

Non accettare tutto:

```
"Questa funzionalità non è nello scope originale.
Possiamo aggiungerla in fase 2."
```

---

## Prevenzione

- **Scope chiaro**: Definisci scope chiaro
- **Change management**: Gestisci cambiamenti formalmente
- **Dì "No"**: Non accettare tutto
- **Fasi**: Organizza in fasi

---

## Origine del termine

Il termine **Scope Creep** deriva dalla gestione progetti e descrive come lo scope "strisci" oltre i requisiti originali.

---

## Termini correlati

- **Feature Creep** - Aggiunta continua di funzionalità
- **YAGNI** - You Aren't Gonna Need It
- **MVP** - Minimum Viable Product

---

## Risorse utili

- [Wikipedia: Scope Creep](https://en.wikipedia.org/wiki/Scope_creep) - Articolo Wikipedia
- [Laravel Project Management](https://laravel.com/docs) - Best practices
