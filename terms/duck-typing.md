# Duck Typing

## Cosa significa

Il **Duck Typing** (tipizzazione anatra) è un principio di programmazione dove il tipo di un oggetto è determinato dal suo comportamento (metodi e proprietà) piuttosto che dalla sua classe. Il nome deriva dal detto: "Se cammina come una papera e starnazza come una papera, allora è una papera".

È quello che succede quando controlli se un oggetto ha certi metodi invece di controllare se è di una certa classe.

---

## Perché ti serve conoscerlo

Conoscere il termine "Duck Typing" ti aiuta a:

- **Capire tipizzazione dinamica** in linguaggi come PHP, Python, JavaScript
- **Scrivere codice più flessibile** che accetta qualsiasi oggetto con il comportamento giusto
- **Comunicare meglio** con il team: "Usiamo duck typing qui"
- **Evitare accoppiamento** a classi specifiche

---

## Come funziona

Il Duck Typing si verifica quando:

- **Controlli comportamento**: Controlli se un oggetto ha certi metodi
- **Non controlli tipo**: Non controlli se è di una certa classe
- **Flessibilità**: Accetti qualsiasi oggetto con il comportamento giusto
- **Polimorfismo**: Usi polimorfismo basato su comportamento

---

## Esempi comuni

### Esempio 1: Duck Typing in PHP

```php
// Duck typing: accetta qualsiasi oggetto con metodo fly()
function makeItFly($bird) {
    // Non controlla se è una classe specifica
    // Controlla solo se ha il metodo fly()
    if (method_exists($bird, 'fly')) {
        $bird->fly();
    }
}

// Funziona con qualsiasi oggetto che ha fly()
class Duck {
    public function fly() { }
}

class Airplane {
    public function fly() { }
}

makeItFly(new Duck());      // Funziona
makeItFly(new Airplane());  // Funziona anche questo!
```

**Vantaggio:** Flessibilità - accetta qualsiasi oggetto con il comportamento giusto.

### Esempio 2: Duck Typing con interfacce

```php
// PHP usa interfacce per duck typing esplicito
interface Flyable {
    public function fly();
}

function makeItFly(Flyable $thing) {
    $thing->fly();
}

// Qualsiasi classe che implementa Flyable funziona
class Duck implements Flyable {
    public function fly() { }
}

class Airplane implements Flyable {
    public function fly() { }
}
```

**Vantaggio:** Duck typing esplicito con type hinting.

### Esempio 3: Duck Typing in Laravel

```php
// Laravel usa duck typing per collections
$collection = collect([1, 2, 3]);

// Non importa il tipo, importa il comportamento
$collection->map(function($item) {
    return $item * 2;
});

// Funziona con array, Collection, o qualsiasi iterabile
```

**Vantaggio:** Flessibilità nelle API Laravel.

---

## Come usarlo

### 1. Controlla comportamento, non tipo

Invece di controllare il tipo, controlla il comportamento:

```php
// Prima: controlla tipo
if ($obj instanceof User) {
    $obj->getName();
}

// Dopo: controlla comportamento (duck typing)
if (method_exists($obj, 'getName')) {
    $obj->getName();
}
```

### 2. Usa interfacce

Usa interfacce per duck typing esplicito:

```php
interface Renderable {
    public function render();
}

function display(Renderable $item) {
    $item->render();
}
```

### 3. Documenta il comportamento atteso

Documenta quale comportamento è atteso:

```php
/**
 * @param object $item Deve avere metodo render()
 */
function display($item) {
    $item->render();
}
```

---

## Prevenzione

- **Interfacce**: Usa interfacce per duck typing esplicito
- **Type hints**: Usa type hints quando possibile
- **Documentazione**: Documenta comportamento atteso
- **Test**: Testa con diversi tipi di oggetti

---

## Origine del termine

Il termine **Duck Typing** deriva dal detto:

> "If it walks like a duck and it quacks like a duck, then it must be a duck"

Il termine è stato reso popolare in Python ma è usato in molti linguaggi dinamici.

---

## Termini correlati

- **Polymorphism** - Polimorfismo
- **Type System** - Sistema di tipi
- **Interface** - Interfacce per duck typing esplicito

---

## Risorse utili

- [Wikipedia: Duck Typing](https://en.wikipedia.org/wiki/Duck_typing) - Articolo Wikipedia
- [PHP Interfaces](https://www.php.net/manual/en/language.oop5.interfaces.php) - Interfacce PHP
- [Laravel Collections](https://laravel.com/docs/collections) - Esempi duck typing

