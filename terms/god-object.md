# God Object

## Cosa significa

Il **God Object** (oggetto divino) è una classe che sa e fa troppe cose, violando il principio di responsabilità singola (Single Responsibility Principle). È un code smell comune che indica che una classe ha troppe responsabilità.

È quello che succede quando una classe diventa onnipotente: conosce tutto, fa tutto, e diventa difficile da testare, mantenere e modificare.

---

## Perché ti serve conoscerlo

Conoscere il termine "God Object" ti aiuta a:

- **Riconoscere classi con troppe responsabilità** che violano SOLID
- **Comunicare meglio** con il team: "Questa classe è un God Object"
- **Identificare quando refactorare** una classe troppo grande
- **Prevenire problemi futuri** evitando di creare classi onnipotenti

---

## Come funziona

Il God Object si verifica quando:

- **Troppe responsabilità**: La classe fa troppe cose diverse
- **Troppe dipendenze**: La classe dipende da troppi altri oggetti
- **Troppo codice**: La classe ha centinaia o migliaia di righe
- **Violazione SRP**: La classe viola il Single Responsibility Principle
- **Difficile da testare**: È difficile testare perché fa troppe cose

---

## Esempi comuni

### Esempio 1: Classe User che fa tutto

```php
// God Object: User fa troppe cose
class User {
    // Gestione autenticazione
    public function login() { }
    public function logout() { }
    public function resetPassword() { }
    
    // Gestione profilo
    public function updateProfile() { }
    public function uploadAvatar() { }
    
    // Gestione ordini
    public function createOrder() { }
    public function cancelOrder() { }
    public function getOrderHistory() { }
    
    // Gestione pagamenti
    public function addPaymentMethod() { }
    public function processPayment() { }
    
    // Gestione notifiche
    public function sendEmail() { }
    public function sendSMS() { }
    
    // ... e così via
}
```

**Problema:** La classe User fa troppe cose e viola SRP.

### Esempio 2: Classe Manager onnipotente

```php
// God Object: Manager gestisce tutto
class OrderManager {
    public function createOrder() { }
    public function updateOrder() { }
    public function deleteOrder() { }
    public function calculateTotal() { }
    public function applyDiscount() { }
    public function processPayment() { }
    public function sendEmail() { }
    public function updateInventory() { }
    public function generateInvoice() { }
    public function trackShipping() { }
    // ... 50+ metodi
}
```

**Problema:** La classe OrderManager ha troppe responsabilità.

---

## Come risolverlo

### 1. Separazione delle responsabilità

Dividi la classe in classi più piccole e focalizzate:

```php
// Prima: God Object
class User {
    public function login() { }
    public function createOrder() { }
    public function sendEmail() { }
}

// Dopo: classi separate
class User {
    // Solo dati utente
}

class AuthenticationService {
    public function login(User $user) { }
}

class OrderService {
    public function createOrder(User $user) { }
}

class NotificationService {
    public function sendEmail(User $user, $message) { }
}
```

### 2. Usa Service Layer

Estrai la logica business in servizi:

```php
// Prima: tutto in OrderManager
class OrderManager {
    public function processOrder() {
        // 200 righe di logica
    }
}

// Dopo: servizi separati
class OrderService {
    public function process(Order $order) {
        $this->paymentService->process($order);
        $this->inventoryService->update($order);
        $this->notificationService->send($order);
    }
}
```

### 3. Applica Single Responsibility Principle

Ogni classe dovrebbe avere una sola responsabilità:

```php
// Ogni classe ha una responsabilità
class OrderRepository {
    // Solo accesso ai dati
}

class OrderCalculator {
    // Solo calcoli
}

class OrderValidator {
    // Solo validazione
}
```

---

## Prevenzione

- **Single Responsibility Principle**: Ogni classe una responsabilità
- **Service Layer**: Usa servizi per logica business
- **Repository Pattern**: Separa accesso ai dati
- **Code review**: Identifica God Object durante le review
- **Refactoring continuo**: Dividi classi grandi in classi più piccole

---

## Origine del termine

Il termine **God Object** deriva dall'anti-pattern "God Class" o "Blob", descritto nel libro "AntiPatterns" (1998) di William Brown.

L'analogia con una divinità è efficace: così come un dio è onnipotente e onnisciente, un God Object sa e fa tutto, rendendolo difficile da gestire.

---

## Termini correlati

- **Code Smell** - Indicatore di problemi nel codice
- **Single Responsibility Principle** - Principio SOLID violato
- **Service Layer** - Pattern per separare responsabilità

---

## Risorse utili

- [Refactoring.Guru: God Object](https://refactoring.guru/smells/large-class) - Spiegazione dettagliata
- [SOLID Principles](https://en.wikipedia.org/wiki/SOLID) - Principi di design
- [Laravel Service Layer](https://laravel.com/docs) - Pattern per Laravel

