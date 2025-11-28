# Bus Factor

## Cosa significa

Il **Bus Factor** (fattore bus) è una metrica che misura quante persone devono essere investite da un bus (o lasciare il team) prima che il progetto sia a rischio. È una misura della conoscenza condivisa nel team e della dipendenza da singole persone.

È quello che succede quando solo una persona sa come funziona una parte critica del sistema, e se quella persona se ne va, il progetto è in pericolo.

---

## Perché ti serve conoscerlo

Conoscere il termine "Bus Factor" ti aiuta a:

- **Identificare rischi** di dipendenza da singole persone
- **Comunicare meglio** con il team: "Questo ha bus factor 1, è rischioso"
- **Pianificare knowledge sharing** per aumentare il bus factor
- **Ridurre rischi** distribuendo conoscenza nel team

---

## Come funziona

Il Bus Factor si calcola come:

- **Bus Factor 1**: Solo una persona sa come funziona → Rischio alto
- **Bus Factor 2**: Due persone sanno → Rischio medio
- **Bus Factor 3+**: Tre o più persone sanno → Rischio basso

---

## Esempi comuni

### Esempio 1: Bus Factor 1

```php
// Solo Marco sa come funziona questo sistema legacy
class LegacyPaymentProcessor {
    // 5000 righe di codice complesso
    // Solo Marco lo capisce
    // Se Marco se ne va, il sistema è a rischio
}
```

**Problema:** Dipendenza critica da una sola persona.

### Esempio 2: Bus Factor 2

```php
// Due persone sanno come funziona
class OrderService {
    // Marco e Luca lo conoscono
    // Se uno se ne va, l'altro può continuare
}
```

**Migliore:** Conoscenza condivisa tra due persone.

### Esempio 3: Bus Factor 3+

```php
// Tre o più persone sanno
class UserService {
    // Marco, Luca, e Sara lo conoscono
    // Rischio molto basso
}
```

**Ideale:** Conoscenza distribuita nel team.

---

## Come migliorarlo

### 1. Pair Programming

Condividi conoscenza attraverso pair programming:

```php
// Invece di: solo una persona lavora
// Fai: pair programming per condividere conoscenza
```

### 2. Code Review

Usa code review per condividere conoscenza:

```php
// Code review permette a tutti di vedere e capire il codice
```

### 3. Documentazione

Documenta codice complesso:

```php
/**
 * Legacy Payment Processor
 * 
 * Questo sistema processa pagamenti legacy.
 * Architettura: [spiegazione]
 * Flusso: [spiegazione]
 */
```

### 4. Knowledge Sharing

Organizza sessioni di knowledge sharing:

```markdown
## Knowledge Sharing Sessions
- Settimana 1: Legacy Payment System (Marco)
- Settimana 2: Order Processing (Luca)
- Settimana 3: User Management (Sara)
```

### 5. Rotazione

Ruota le persone su parti diverse del sistema:

```markdown
## Rotazione
- Q1: Marco su Payment, Luca su Order
- Q2: Marco su Order, Luca su Payment
```

---

## Prevenzione

- **Pair Programming**: Condividi conoscenza durante lo sviluppo
- **Code Review**: Tutti vedono e capiscono il codice
- **Documentazione**: Documenta parti complesse
- **Knowledge Sharing**: Sessioni regolari di condivisione
- **Rotazione**: Ruota persone su parti diverse

---

## Origine del termine

Il termine **Bus Factor** deriva dalla domanda: "Quante persone devono essere investite da un bus prima che il progetto sia a rischio?"

L'analogia con il bus è efficace: così come un incidente con un bus può colpire più persone, il bus factor misura quante persone possono "lasciare" prima che il progetto sia in pericolo.

---

## Termini correlati

- **Knowledge Sharing** - Condivisione di conoscenza
- **Pair Programming** - Programmazione in coppia
- **Code Review** - Revisione del codice

---

## Risorse utili

- [Wikipedia: Bus Factor](https://en.wikipedia.org/wiki/Bus_factor) - Articolo Wikipedia
- [Laravel Team Practices](https://laravel.com/docs) - Best practices team
- [Pair Programming Guide](https://martinfowler.com/articles/on-pair-programming.html) - Guida pair programming

