# Mojibake

## Indice

### Comprensione Base
- [Cosa significa](#cosa-significa)
- [Perché ti serve conoscerlo](#perché-ti-serve-conoscerlo)
- [Come funziona](#come-funziona)
- [Esempi visivi](#esempi-visivi)

### Contesto Pratico
- [Quando lo vedi](#quando-lo-vedi)
- [Come riconoscerlo](#come-riconoscerlo)
- [Casi d'uso comuni](#casi-duso-comuni)
- [Esempi reali](#esempi-reali)

### Risoluzione
- [Come risolverlo](#come-risolverlo)
- [Prevenzione](#prevenzione)
- [Best practices](#best-practices)

### Approfondimenti
- [Origine del termine](#origine-del-termine)
- [Termini correlati](#termini-correlati)
- [Risorse utili](#risorse-utili)

---

## Cosa significa

Il **Mojibake** (文字化け) è il fenomeno per cui i caratteri vengono visualizzati in modo corrotto o illeggibile a causa di problemi di encoding. Letteralmente significa "caratteri trasformati" o "caratteri corrotti" in giapponese.

È quello che succede quando vedi caratteri strani al posto di lettere accentate, simboli al posto di caratteri speciali, o quando un testo in una lingua viene visualizzato con caratteri completamente diversi.

---

## Perché ti serve conoscerlo

Conoscere il termine "Mojibake" ti aiuta a:

- **Comunicare meglio** con il team: invece di dire "i caratteri sono storti" o "l'encoding è rotto", puoi dire "abbiamo un problema di Mojibake"
- **Cercare soluzioni** più efficacemente: sapere il nome tecnico ti permette di trovare risorse e soluzioni specifiche
- **Riconoscere il problema** più velocemente: quando vedi caratteri corrotti, sai subito che è un problema di encoding
- **Prevenire il problema** in futuro: capendo la causa, puoi evitare che si ripresenti

---

## Come funziona

Il Mojibake si verifica quando c'è una **discrepanza tra l'encoding usato per salvare/scrivere i dati e quello usato per leggerli**.

**Flusso del problema:**

```
1. File salvato con encoding A (es. UTF-8)
   ↓
2. File letto con encoding B (es. ISO-8859-1)
   ↓
3. Sistema interpreta i byte in modo sbagliato
   ↓
4. Caratteri visualizzati in modo corrotto (Mojibake)
```

**Esempio pratico:**

Il carattere "è" in UTF-8 è rappresentato da due byte: `0xC3 0xA8`

Se questi byte vengono letti come ISO-8859-1:
- `0xC3` diventa "Ã"
- `0xA8` diventa "¨"

Risultato: "è" diventa "Ã¨"

---

## Esempi visivi

### Esempio 1: Testo italiano corrotto

**Originale:**
```
Ciao, come stai? È una bella giornata!
```

**Con Mojibake:**
```
Ciao, come stai? Ãˆ una bella giornata!
```

### Esempio 2: Caratteri giapponesi corrotti

**Originale:**
```
こんにちは
```

**Con Mojibake:**
```
ããã«ã¡ã¯
```

### Esempio 3: Simboli corrotti

**Originale:**
```
€ 100,00
```

**Con Mojibake:**
```
â‚¬ 100,00
```

---

## Quando lo vedi

Il Mojibake si manifesta comunemente in queste situazioni:

- **File di testo** aperti con l'editor sbagliato o con encoding diverso
- **Dati dal database** quando il charset non è configurato correttamente
- **Risposte HTTP** quando il Content-Type header non specifica il charset corretto
- **Email** quando il client non gestisce correttamente l'encoding
- **File CSV/Excel** importati con encoding diverso da quello originale
- **API** che ricevono o inviano dati con encoding diverso
- **File di configurazione** letti con encoding sbagliato
- **Log** quando il sistema di logging usa un encoding diverso

---

## Come riconoscerlo

Sintomi tipici che indicano un problema di Mojibake:

- **Caratteri accentati corrotti**: "è" diventa "Ã¨", "à" diventa "Ã "
- **Simboli strani**: "€" diventa "â‚¬", "©" diventa "Â©"
- **Caratteri giapponesi/cinesi corrotti**: caratteri completamente diversi o simboli strani
- **Spazi o caratteri invisibili** al posto di caratteri normali
- **Sequenze ripetute**: pattern come "Ã¨" o "â‚¬" che appaiono frequentemente
- **Testo parzialmente corrotto**: alcune parti sono corrette, altre no
- **Differenze tra ambienti**: stesso file corretto in un ambiente, corrotto in un altro

**Pattern comuni:**
- `Ã¨` invece di `è`
- `Ã ` invece di `à`
- `Ã©` invece di `é`
- `â‚¬` invece di `€`
- `Â©` invece di `©`

---

## Casi d'uso comuni

### 1. Sviluppo Web (Laravel/PHP)

**Scenario:** Dati salvati nel database con UTF-8 ma letti come ISO-8859-1

```php
// Database configurato con charset utf8mb4
// Ma la connessione usa latin1
DB::connection()->getPdo()->exec("SET NAMES 'latin1'");
```

**Risultato:** Caratteri accentati corrotti nelle query e nelle risposte.

### 2. Import/Export CSV

**Scenario:** File CSV salvato con encoding Windows-1252 ma importato come UTF-8

**Risultato:** Nomi, indirizzi e altri dati con caratteri speciali corrotti.

### 3. API Integration

**Scenario:** API che invia dati in UTF-8 ma il client li interpreta come ISO-8859-1

**Risultato:** JSON con caratteri corrotti, errori di parsing, dati illeggibili.

### 4. Email

**Scenario:** Email inviata con charset UTF-8 ma client email che legge ISO-8859-1

**Risultato:** Oggetto e corpo dell'email con caratteri corrotti.

---

## Esempi reali

### Esempio 1: Database Laravel

**Problema:** Nomi utente con caratteri accentati salvati correttamente ma visualizzati corrotti.

**Causa:** Database configurato con `charset=utf8mb4` ma connessione PHP che usa `latin1`.

**Soluzione:**
```php
// config/database.php
'mysql' => [
    'charset' => 'utf8mb4',
    'collation' => 'utf8mb4_unicode_ci',
    // ...
]
```

### Esempio 2: File di configurazione

**Problema:** File `.env` con caratteri speciali corrotti quando letto da script.

**Causa:** File salvato con encoding diverso da quello usato dallo script.

**Soluzione:** Salvare sempre i file di configurazione in UTF-8.

### Esempio 3: API Response

**Problema:** Risposta JSON con caratteri corrotti quando consumata da client.

**Causa:** Header HTTP senza specificare il charset o charset sbagliato.

**Soluzione:**
```php
return response()->json($data)
    ->header('Content-Type', 'application/json; charset=utf-8');
```

---

## Come risolverlo

### 1. Verificare l'encoding del file sorgente

**Per file di testo:**
- Apri il file con un editor che mostra l'encoding (VS Code, Sublime Text, Notepad++)
- Verifica l'encoding corrente
- Converti in UTF-8 se necessario

**Per database:**
```sql
-- Verifica charset e collation
SHOW CREATE DATABASE nome_database;
SHOW CREATE TABLE nome_tabella;

-- Verifica charset delle colonne
SHOW FULL COLUMNS FROM nome_tabella;
```

### 2. Configurare correttamente il charset

**Laravel - Database:**
```php
// config/database.php
'mysql' => [
    'charset' => 'utf8mb4',
    'collation' => 'utf8mb4_unicode_ci',
]
```

**Laravel - Response HTTP:**
```php
// In middleware o bootstrap
header('Content-Type: text/html; charset=utf-8');
```

**PHP - File:**
```php
// Leggere file con encoding corretto
$content = mb_convert_encoding(
    file_get_contents('file.txt'),
    'UTF-8',
    'ISO-8859-1'
);
```

### 3. Convertire dati esistenti

**Database:**
```sql
-- Converti database a UTF-8
ALTER DATABASE nome_database CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Converti tabella
ALTER TABLE nome_tabella CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Converti colonna
ALTER TABLE nome_tabella MODIFY nome_colonna VARCHAR(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

**PHP - Conversione:**
```php
// Converti stringa da encoding a UTF-8
$converted = mb_convert_encoding($string, 'UTF-8', 'ISO-8859-1');

// Oppure con iconv
$converted = iconv('ISO-8859-1', 'UTF-8', $string);
```

### 4. Verificare header HTTP

**Laravel:**
```php
// In middleware
return $next($request)
    ->header('Content-Type', 'text/html; charset=utf-8');
```

**Blade:**
```blade
<meta charset="utf-8">
```

---

## Prevenzione

Per evitare problemi di Mojibake:

### 1. Standardizzare su UTF-8

- **Sempre UTF-8** per tutti i file, database, API e comunicazioni
- UTF-8 è lo standard de facto e supporta tutti i caratteri Unicode

### 2. Configurare correttamente l'ambiente

**Laravel:**
- Database con `charset=utf8mb4` e `collation=utf8mb4_unicode_ci`
- Response HTTP con header `Content-Type` corretto
- File di configurazione in UTF-8

**Editor:**
- Configurare l'editor per salvare sempre in UTF-8
- Verificare l'encoding prima di salvare file importanti

### 3. Validare l'encoding

**PHP:**
```php
// Verifica se una stringa è UTF-8 valida
if (!mb_check_encoding($string, 'UTF-8')) {
    // Converti o gestisci l'errore
    $string = mb_convert_encoding($string, 'UTF-8', 'auto');
}
```

### 4. Testare con caratteri speciali

- Includere sempre caratteri accentati, simboli e caratteri Unicode nei test
- Verificare che l'encoding sia corretto in tutti gli ambienti (dev, staging, production)

---

## Best practices

### 1. Usa UTF-8 ovunque

UTF-8 è lo standard moderno e supporta tutti i caratteri Unicode. Evita altri encoding a meno che non ci siano vincoli specifici.

### 2. Configurazione centralizzata

Centralizza la configurazione dell'encoding in un unico punto:

```php
// config/app.php o bootstrap
mb_internal_encoding('UTF-8');
mb_http_output('UTF-8');
```

### 3. Validazione input

Valida sempre che l'input sia in UTF-8 valido:

```php
if (!mb_check_encoding($input, 'UTF-8')) {
    throw new InvalidArgumentException('Input must be valid UTF-8');
}
```

### 4. Header HTTP espliciti

Specifica sempre il charset negli header HTTP:

```php
Content-Type: application/json; charset=utf-8
Content-Type: text/html; charset=utf-8
```

### 5. Database consistency

Assicurati che database, connessioni e applicazione usino lo stesso encoding:

```php
// Verifica configurazione
DB::select("SHOW VARIABLES LIKE 'character_set%'");
```

### 6. Logging

Configura il logging per usare UTF-8:

```php
// config/logging.php
'channels' => [
    'single' => [
        'driver' => 'single',
        'path' => storage_path('logs/laravel.log'),
        'level' => 'debug',
    ],
]
```

---

## Origine del termine

Il termine **Mojibake** (文字化け) deriva dal giapponese:
- **文字** (moji) = carattere, lettera
- **化け** (bake) = trasformazione, corruzione

Letteralmente significa "caratteri trasformati" o "caratteri corrotti".

Il termine è diventato comune perché il problema era particolarmente evidente con i caratteri giapponesi, che richiedono encoding specifici. Quando l'encoding era sbagliato, i caratteri giapponesi diventavano completamente illeggibili, rendendo il problema molto visibile.

Oggi il termine è usato universalmente per descrivere qualsiasi corruzione di caratteri dovuta a problemi di encoding, non solo per il giapponese.

---

## Termini correlati

- **Encoding** - Sistema di codifica dei caratteri
- **Character Set** - Insieme di caratteri disponibili
- **Collation** - Regole di confronto e ordinamento dei caratteri
- **Unicode** - Standard per la codifica dei caratteri
- **BOM (Byte Order Mark)** - Marcatore di ordine dei byte

---

## Risorse utili

### Documentazione

- **UTF-8 Everywhere**  
  [https://utf8everywhere.org/](https://utf8everywhere.org/) - Guida completa su UTF-8

- **Unicode Consortium**  
  [https://unicode.org/](https://unicode.org/) - Standard Unicode ufficiale

- **PHP: Multibyte String**  
  [https://www.php.net/manual/en/book.mbstring.php](https://www.php.net/manual/en/book.mbstring.php) - Funzioni PHP per multibyte

- **Laravel: Database Configuration**  
  [https://laravel.com/docs/database#configuration](https://laravel.com/docs/database#configuration) - Configurazione database Laravel

### Articoli e Guide

- **Wikipedia: Mojibake**  
  [https://en.wikipedia.org/wiki/Mojibake](https://en.wikipedia.org/wiki/Mojibake) - Articolo Wikipedia completo

- **The Absolute Minimum Every Software Developer Must Know About Unicode**  
  [https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/) - Guida essenziale su Unicode

- **Character Encoding: The Secret Behind Computer Text**  
  [https://www.smashingmagazine.com/2012/06/all-about-unicode-utf8-character-sets/](https://www.smashingmagazine.com/2012/06/all-about-unicode-utf8-character-sets/) - Articolo approfondito su encoding

### Strumenti

- **Encoding Detector**  
  [https://www.freeformatter.com/encoding-detector.html](https://www.freeformatter.com/encoding-detector.html) - Rileva l'encoding di un file

- **Character Encoding Converter**  
  [https://www.freeformatter.com/encoding-converter.html](https://www.freeformatter.com/encoding-converter.html) - Converti tra encoding diversi

- **UTF-8 Validator**  
  [https://www.freeformatter.com/utf-8-validator.html](https://www.freeformatter.com/utf-8-validator.html) - Valida stringhe UTF-8

---

> **Contribuisci:**  
> Se hai esempi, casi d'uso o soluzioni da condividere, apri una PR e arricchisci questa documentazione!

