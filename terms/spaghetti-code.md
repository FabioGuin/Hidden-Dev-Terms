# Spaghetti Code

## Cosa significa

Il **Spaghetti Code** (codice spaghetti) è codice intrecciato, difficile da seguire e mantenere. Il nome deriva dall'analogia con gli spaghetti: così come gli spaghetti sono intrecciati e difficili da separare, il codice è intrecciato e difficile da capire.

È quello che succede quando il codice ha flussi di controllo complessi, goto, o logica così intrecciata che è difficile capire cosa fa e come funziona.

---

## Perché ti serve conoscerlo

Conoscere il termine "Spaghetti Code" ti aiuta a:

- **Riconoscere codice difficile da mantenere** con flussi complessi
- **Comunicare meglio** con il team: "Questo è spaghetti code, dobbiamo refactorare"
- **Identificare quando refactorare** codice troppo complesso
- **Prevenire problemi futuri** evitando di creare codice intrecciato

---

## Come funziona

Lo Spaghetti Code si verifica quando:

- **Flussi di controllo complessi**: Troppi if annidati, switch complessi
- **Goto e salti**: Uso di goto o break/continue eccessivi
- **Logica intrecciata**: Codice dove tutto dipende da tutto
- **Nessuna struttura**: Mancanza di pattern o architettura chiara
- **Difficile da testare**: Impossibile testare unità isolate

---

## Esempi comuni

### Esempio 1: If annidati profondi

```php
// Spaghetti code: troppi if annidati
public function processOrder($order) {
    if ($order) {
        if ($order->status == 'pending') {
            if ($order->user) {
                if ($order->user->isActive()) {
                    if ($order->total > 0) {
                        if ($order->items) {
                            foreach ($order->items as $item) {
                                if ($item->quantity > 0) {
                                    // Logica qui, 8 livelli di indentazione!
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

**Problema:** Troppi livelli di annidamento rendono il codice difficile da seguire.

### Esempio 2: Goto e salti

```php
// Spaghetti code: uso di break/continue eccessivo
public function processData($data) {
    foreach ($data as $item) {
        if (!$item->isValid()) {
            continue; // Salta
        }
        
        foreach ($item->subItems as $subItem) {
            if ($subItem->hasError()) {
                break; // Esce dal loop
            }
            
            if ($subItem->needsProcessing()) {
                goto process; // Salto
            }
        }
        
        process:
        // Logica qui
    }
}
```

**Problema:** Flussi di controllo difficili da seguire.

### Esempio 3: Logica intrecciata

```php
// Spaghetti code: tutto dipende da tutto
public function calculateTotal($order) {
    $total = 0;
    $discount = 0;
    $tax = 0;
    
    // Calcolo totale
    foreach ($order->items as $item) {
        $total += $item->price * $item->quantity;
    }
    
    // Calcolo sconto (dipende da totale)
    if ($total > 100) {
        $discount = $total * 0.10;
    }
    
    // Calcolo tasse (dipende da totale e sconto)
    $tax = ($total - $discount) * 0.20;
    
    // Aggiornamento totale (dipende da tutto)
    $total = $total - $discount + $tax;
    
    // Aggiornamento order (dipende da tutto)
    $order->total = $total;
    $order->discount = $discount;
    $order->tax = $tax;
    
    // Salvataggio (dipende da tutto)
    $order->save();
    
    // Invio email (dipende da tutto)
    Mail::send($order);
    
    return $total;
}
```

**Problema:** Tutto è intrecciato e difficile da testare.

---

## Come risolverlo

### 1. Early return

Riduci l'annidamento con early return:

```php
// Prima: if annidati
public function processOrder($order) {
    if ($order) {
        if ($order->status == 'pending') {
            if ($order->user) {
                // Logica
            }
        }
    }
}

// Dopo: early return
public function processOrder($order) {
    if (!$order) {
        return;
    }
    
    if ($order->status != 'pending') {
        return;
    }
    
    if (!$order->user) {
        return;
    }
    
    // Logica qui, nessun annidamento
}
```

### 2. Estrai metodi

Dividi la logica complessa in metodi più piccoli:

```php
// Prima: tutto in un metodo
public function processOrder($order) {
    // 200 righe di logica intrecciata
}

// Dopo: metodi separati
public function processOrder($order) {
    $this->validateOrder($order);
    $this->calculateTotal($order);
    $this->applyDiscount($order);
    $this->saveOrder($order);
    $this->sendNotification($order);
}
```

### 3. Usa pattern

Applica pattern per strutturare il codice:

```php
// Prima: logica intrecciata
public function calculateTotal($order) {
    // Tutto mescolato
}

// Dopo: pattern Strategy
class OrderCalculator {
    public function calculate(Order $order, DiscountStrategy $discount): float {
        $total = $this->sumItems($order);
        $discountAmount = $discount->calculate($total);
        return $total - $discountAmount;
    }
}
```

---

## Prevenzione

- **Early return**: Riduci l'annidamento
- **Metodi piccoli**: Ogni metodo una responsabilità
- **Pattern**: Usa pattern per strutturare
- **Test**: Scrivi test che rivelano complessità
- **Code review**: Identifica spaghetti code durante le review

---

## Origine del termine

Il termine **Spaghetti Code** è stato coniato nella programmazione per descrivere codice intrecciato e difficile da seguire.

L'analogia con gli spaghetti è efficace: così come gli spaghetti sono intrecciati e difficili da separare, il codice spaghetti è intrecciato e difficile da capire e modificare.

---

## Termini correlati

- **Code Smell** - Indicatore di problemi nel codice
- **God Object** - Classe che fa troppe cose
- **Refactoring** - Processo di miglioramento del codice

---

## Risorse utili

- [Refactoring.Guru: Spaghetti Code](https://refactoring.guru/smells/long-method) - Spiegazione dettagliata
- [Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882) - Libro su codice pulito
- [Laravel Best Practices](https://laravel.com/docs) - Best practices Laravel

