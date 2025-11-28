# N+1 Problem

## Cosa significa

Il **N+1 Problem** (problema N+1) è un problema di performance comune quando si caricano dati relazionali. Si verifica quando esegui 1 query per ottenere N record, e poi N query aggiuntive (una per ogni record) per caricare le relazioni. Il risultato è N+1 query invece di 2 query ottimizzate.

È quello che succede quando carichi una lista di utenti e poi, per ogni utente, fai una query separata per caricare i suoi ordini, invece di caricare tutto con una o due query ottimizzate.

---

## Perché ti serve conoscerlo

Conoscere il termine "N+1 Problem" ti aiuta a:

- **Riconoscere problemi di performance** comuni con ORM come Eloquent
- **Comunicare meglio** con il team: "Abbiamo un N+1 problem qui"
- **Ottimizzare query** usando eager loading invece di lazy loading
- **Evitare problemi di performance** in produzione

---

## Come funziona

Il N+1 Problem si verifica quando:

- **Query principale**: 1 query per ottenere N record (es. 100 utenti)
- **Query per relazione**: N query aggiuntive (una per ogni record) per caricare relazioni
- **Risultato**: N+1 query totali invece di 2 query ottimizzate

**Esempio:**
- 1 query per ottenere 100 utenti
- 100 query per ottenere gli ordini di ogni utente
- Totale: 101 query invece di 2

---

## Esempi comuni

### Esempio 1: N+1 Problem con Eloquent

```php
// N+1 Problem: 1 query + N query per relazione
$users = User::all(); // 1 query: SELECT * FROM users

foreach ($users as $user) {
    // N query: una per ogni utente
    $orders = $user->orders; // SELECT * FROM orders WHERE user_id = ?
    // Totale: 1 + 100 = 101 query per 100 utenti
}
```

**Problema:** 101 query invece di 2.

### Esempio 2: N+1 Problem in Blade

```blade
{{-- N+1 Problem: ogni iterazione fa una query --}}
@foreach($users as $user)
    <div>
        <h3>{{ $user->name }}</h3>
        <ul>
            @foreach($user->orders as $order) {{-- Query qui! --}}
                <li>{{ $order->total }}</li>
            @endforeach
        </ul>
    </div>
@endforeach
```

**Problema:** Ogni `$user->orders` genera una query separata.

### Esempio 3: N+1 Problem con relazioni annidate

```php
// N+1 Problem: relazioni annidate
$orders = Order::all(); // 1 query

foreach ($orders as $order) {
    $user = $order->user; // N query per user
    $items = $order->items; // N query per items
    
    foreach ($items as $item) {
        $product = $item->product; // N*M query per products
    }
}
```

**Problema:** Query esponenziali (1 + N + N + N*M).

---

## Come risolverlo

### 1. Eager Loading con `with()`

Usa `with()` per caricare relazioni in anticipo:

```php
// Prima: N+1 Problem
$users = User::all();
foreach ($users as $user) {
    $orders = $user->orders; // Query per ogni utente
}

// Dopo: Eager Loading (2 query totali)
$users = User::with('orders')->get();
// 1 query: SELECT * FROM users
// 1 query: SELECT * FROM orders WHERE user_id IN (...)
foreach ($users as $user) {
    $orders = $user->orders; // Nessuna query, già caricato
}
```

### 2. Eager Loading con relazioni annidate

Carica anche relazioni annidate:

```php
// Eager loading con relazioni annidate
$orders = Order::with(['user', 'items.product'])->get();
// 1 query: orders
// 1 query: users
// 1 query: items
// 1 query: products
// Totale: 4 query invece di centinaia
```

### 3. Eager Loading condizionale

Carica relazioni solo quando necessario:

```php
// Eager loading condizionale
$users = User::with(['orders' => function ($query) {
    $query->where('status', 'completed');
}])->get();
```

### 4. Lazy Eager Loading

Carica relazioni dopo la query principale:

```php
// Lazy eager loading
$users = User::all();
$users->load('orders'); // Carica relazioni dopo
```

### 5. Join invece di relazioni

Per casi complessi, usa join:

```php
// Join invece di relazioni
$users = User::join('orders', 'users.id', '=', 'orders.user_id')
    ->select('users.*', 'orders.total')
    ->get();
```

---

## Prevenzione

- **Sempre eager loading**: Usa `with()` quando carichi relazioni
- **Laravel Debugbar**: Usa Laravel Debugbar per identificare N+1
- **Code review**: Controlla query durante code review
- **Test performance**: Testa performance con dati reali
- **Monitoring**: Monitora query in produzione

---

## Come identificarlo

### 1. Laravel Debugbar

Laravel Debugbar mostra tutte le query:

```
Queries: 101
Time: 2.5s
```

Se vedi molte query simili, hai un N+1 Problem.

### 2. Log delle query

Abilita query logging:

```php
DB::enableQueryLog();
// ... tuo codice ...
dd(DB::getQueryLog());
```

### 3. Telescope

Laravel Telescope mostra query e performance:

```
Queries: 101
Slow queries: 50
```

### 4. Pattern riconoscibili

Cerca pattern come:

```php
// Pattern sospetto
foreach ($items as $item) {
    $relation = $item->relation; // Query qui
}
```

---

## Origine del termine

Il termine **N+1 Problem** deriva dalla descrizione matematica del problema:
- **1 query** per ottenere N record
- **N query** aggiuntive per relazioni
- **Totale: N+1 query**

Il termine è diventato comune nella comunità di sviluppo per descrivere questo problema di performance con ORM.

---

## Termini correlati

- **Eager Loading** - Caricare relazioni in anticipo
- **Lazy Loading** - Caricare relazioni on-demand (causa N+1)
- **Query Optimization** - Ottimizzazione delle query

---

## Risorse utili

- [Laravel: Eager Loading](https://laravel.com/docs/eloquent-relationships#eager-loading) - Documentazione ufficiale
- [Laravel Debugbar](https://github.com/barryvdh/laravel-debugbar) - Tool per identificare N+1
- [Laravel Telescope](https://laravel.com/docs/telescope) - Debugging e monitoring
- [Wikipedia: N+1 Problem](https://en.wikipedia.org/wiki/N%2B1_query_problem) - Articolo Wikipedia

