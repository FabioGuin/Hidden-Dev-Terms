# Premature Optimization

## Cosa significa

La **Premature Optimization** (ottimizzazione prematura) è l'atto di ottimizzare il codice prima che sia necessario o prima di avere dati che dimostrino che l'ottimizzazione è necessaria. È un anti-pattern comune che può rendere il codice più complesso senza benefici reali.

È quello che succede quando ottimizzi tutto subito, anche se non serve, rendendo il codice più complesso e difficile da mantenere.

---

## Perché ti serve conoscerlo

Conoscere il termine "Premature Optimization" ti aiuta a:

- **Evitare ottimizzazioni inutili** che complicano il codice
- **Comunicare meglio** con il team: "Questa è premature optimization, ottimizziamo solo se necessario"
- **Focalizzarti sulla funzionalità** prima dell'ottimizzazione
- **Misurare prima di ottimizzare** usando dati reali

---

## Come funziona

La Premature Optimization si verifica quando:

- **Ottimizzi senza misurare**: Ottimizzi senza sapere se c'è un problema
- **Complessità inutile**: Aggiungi complessità per performance che non servono
- **YAGNI violato**: Implementi ottimizzazioni che non servono ora
- **Focus sbagliato**: Ti concentri su performance invece di funzionalità

---

## Esempi comuni

### Esempio 1: Cache prematura

```php
// Premature optimization: cache senza sapere se serve
public function getUser($id) {
    return Cache::remember("user_{$id}", 3600, function () use ($id) {
        return User::find($id);
    });
}

// Problema: La query è veloce, la cache non serve
// Complessità aggiunta senza benefici
```

**Problema:** Cache aggiunta senza misurare se serve.

### Esempio 2: Query optimization prematura

```php
// Premature optimization: query complessa per "performance"
$users = DB::table('users')
    ->select('id', 'name')
    ->join('profiles', 'users.id', '=', 'profiles.user_id')
    ->where('users.active', true)
    ->whereIn('profiles.role', ['admin', 'user'])
    ->groupBy('users.id')
    ->havingRaw('COUNT(profiles.id) > 0')
    ->get();

// Problema: Query complessa quando una semplice funzionerebbe
// $users = User::with('profile')->where('active', true)->get();
```

**Problema:** Query ottimizzata senza sapere se serve.

### Esempio 3: Micro-ottimizzazioni

```php
// Premature optimization: micro-ottimizzazioni inutili
// Invece di:
$result = [];
foreach ($items as $item) {
    $result[] = $item->value;
}

// Ottimizzi prematuramente:
$result = array_map(function($item) {
    return $item->value;
}, $items);

// Problema: Differenza trascurabile, codice meno leggibile
```

**Problema:** Micro-ottimizzazioni che non migliorano performance reali.

---

## Come evitarla

### 1. Misura prima di ottimizzare

Usa profiling per identificare colli di bottiglia reali:

```php
// Misura prima
$start = microtime(true);
$result = expensiveOperation();
$time = microtime(true) - $start;

// Se è lento, allora ottimizza
if ($time > 1.0) {
    // Ottimizza qui
}
```

### 2. Segui YAGNI

Non implementare ottimizzazioni che non servono ora:

```php
// Prima: funziona
public function getUser($id) {
    return User::find($id);
}

// Dopo (solo se necessario): ottimizza
public function getUser($id) {
    return Cache::remember("user_{$id}", 3600, function () use ($id) {
        return User::find($id);
    });
}
```

### 3. Focus su funzionalità

Concentrati sulla funzionalità prima della performance:

```php
// Prima: funziona correttamente
// Dopo: ottimizza solo se necessario
```

### 4. Usa principio 80/20

Ottimizza solo le parti che contano:

```php
// Identifica i 20% del codice che usa 80% delle risorse
// Ottimizza solo quello
```

---

## Quando è accettabile

Non tutta l'ottimizzazione è prematura:

- **Best practices**: Seguire best practices non è premature optimization
- **Architettura**: Progettare architettura scalabile non è premature
- **Pattern consolidati**: Usare pattern noti non è premature
- **Ottimizzazioni ovvie**: Alcune ottimizzazioni sono ovvie e sicure

---

## Origine del termine

Il termine **Premature Optimization** è stato reso popolare da **Donald Knuth** con la famosa citazione:

> "Premature optimization is the root of all evil"

La citazione completa è: "We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%."

---

## Termini correlati

- **YAGNI** - You Aren't Gonna Need It
- **Technical Debt** - Debito tecnico
- **Bikeshedding** - Perdere tempo su dettagli

---

## Risorse utili

- [Donald Knuth: Premature Optimization](https://en.wikiquote.org/wiki/Donald_Knuth) - Citazione originale
- [Laravel Performance](https://laravel.com/docs/performance) - Guida performance Laravel
- [PHP Profiling](https://www.php.net/manual/en/features.profiling.php) - Profiling PHP

