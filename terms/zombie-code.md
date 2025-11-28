# Zombie Code

## Cosa significa

Lo **Zombie Code** (codice zombie) è codice che dovrebbe essere morto (non più necessario) ma continua a essere eseguito, causando problemi o comportamenti inaspettati. A differenza del Dead Code, lo Zombie Code è ancora attivo.

È quello che succede quando codice vecchio o deprecato continua a funzionare e interferisce con il nuovo codice, creando bug o comportamenti strani.

---

## Perché ti serve conoscerlo

Conoscere il termine "Zombie Code" ti aiuta a:

- **Riconoscere codice deprecato** che continua a essere eseguito
- **Comunicare meglio** con il team: "Abbiamo zombie code che interferisce"
- **Identificare codice legacy** che dovrebbe essere rimosso
- **Prevenire problemi** rimuovendo codice obsoleto

---

## Come funziona

Lo Zombie Code si verifica quando:

- **Codice deprecato**: Codice marcato come deprecato ma ancora attivo
- **Legacy code**: Codice vecchio che non dovrebbe essere usato
- **Backward compatibility**: Codice mantenuto per compatibilità ma problematico
- **Feature flag**: Codice vecchio ancora attivo tramite flag
- **Codice nascosto**: Codice che non si sa sia ancora attivo

---

## Esempi comuni

### Esempio 1: Codice deprecato ancora attivo

```php
// Zombie code: funzione deprecata ma ancora chiamata
/**
 * @deprecated Use calculateNewTotal() instead
 */
public function calculateTotal($items) {
    // Logica vecchia ancora eseguita
    return array_sum(array_column($items, 'price'));
}

// Nuova funzione
public function calculateNewTotal($items) {
    // Logica nuova
}

// Ma la vecchia è ancora chiamata da qualche parte
calculateTotal($items); // Zombie code!
```

**Problema:** Codice deprecato ancora in uso.

### Esempio 2: Feature flag non rimosso

```php
// Zombie code: feature flag vecchio ancora attivo
if (config('features.old_payment_method')) {
    // Codice vecchio che non dovrebbe essere usato
    $this->processOldPayment($order);
} else {
    // Codice nuovo
    $this->processNewPayment($order);
}

// Il flag è ancora true da qualche parte!
```

**Problema:** Feature flag vecchio ancora attivo.

### Esempio 3: Codice legacy nascosto

```php
// Zombie code: codice legacy che interferisce
class OrderProcessor {
    public function process($order) {
        // Nuovo codice
        $this->processNewWay($order);
    }
    
    // Zombie code: metodo privato ancora chiamato da qualche parte
    private function processOldWay($order) {
        // Logica vecchia che interferisce
    }
}
```

**Problema:** Codice vecchio ancora attivo.

---

## Come risolverlo

### 1. Rimuovi codice deprecato

Se il codice è deprecato, rimuovilo dopo un periodo di transizione:

```php
// Rimuovi dopo aver migrato tutti i chiamanti
// public function calculateTotal($items) { } // Rimosso
```

### 2. Disabilita feature flag

Disabilita feature flag vecchi:

```php
// Rimuovi il flag o impostalo a false
// 'old_payment_method' => false,
```

### 3. Trova tutti i chiamanti

Usa strumenti per trovare tutti i chiamanti:

```bash
# Cerca tutti i riferimenti
grep -r "calculateTotal" app/
```

### 4. Migrazione graduale

Migra gradualmente dal vecchio al nuovo:

```php
// Fase 1: Depreca
@deprecated

// Fase 2: Logga uso
Log::warning('Deprecated function called');

// Fase 3: Rimuovi
```

---

## Prevenzione

- **Deprecazione chiara**: Marca codice deprecato chiaramente
- **Periodo di transizione**: Dà tempo per migrare
- **Monitoring**: Monitora uso di codice deprecato
- **Documentazione**: Documenta quando rimuovere
- **Code review**: Identifica zombie code durante le review

---

## Origine del termine

Il termine **Zombie Code** deriva dall'analogia con gli zombie: così come gli zombie sono morti ma ancora attivi, zombie code è codice che dovrebbe essere morto ma continua a essere eseguito.

---

## Termini correlati

- **Dead Code** - Codice che non viene mai eseguito (opposto)
- **Legacy Code** - Codice vecchio da mantenere
- **Technical Debt** - Debito tecnico accumulato

---

## Risorse utili

- [PHP Deprecation](https://www.php.net/manual/en/migration80.deprecated.php) - Gestione deprecazioni
- [Laravel Deprecations](https://laravel.com/docs/upgrade) - Gestione deprecazioni Laravel
