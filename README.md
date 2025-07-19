# 🧩 CruciCerca - Tool per Cruciverba

Un potente strumento Python per **creare e risolvere cruciverba** utilizzando pattern avanzati e wildcard intelligenti.

## ✨ Caratteristiche Principali

### 🔍 **Ricerca Avanzata con Wildcard**
- **`*`** = qualsiasi carattere
- **`@`** = vocale (a, e, i, o, u)  
- **`#`** = consonante (tutte le altre lettere)
- **`-testo`** = sottostringa con filtri di lunghezza opzionali

### 📚 **Multi-Dizionario Automatico**
- Caricamento automatico di tutti i file `.txt` dalla cartella `dizionari/`
- Supporto per più lingue contemporaneamente
- Risultati organizzati per dizionario con statistiche

### 🎨 **Interface User-Friendly**
- Output colorato e organizzato con emoji
- Statistiche dettagliate per ogni ricerca
- Modalità ricerca interattiva integrata

## 🚀 Installazione e Setup

### Requisiti
- **Python 3.6+**
- **Jupyter Notebook**
- Librerie standard: `os`, `glob`

### Quick Start

1. **Clona o scarica** questo repository
2. **Crea la cartella 'dizionari/' e popolala con i tuoi file in formato .txt** (vedi sezione [Dizionari](#-dizionari))
4. **Apri il notebook**: `ricerca_parole.ipynb`
5. **Esegui le celle** nell'ordine:
   - Cella 3: Carica funzioni di importazione
   - Cella 5: Carica funzioni di ricerca  
   - Cella 8: Carica tutti i dizionari
   - Cella 11: Inizia la ricerca interattiva!

## 📖 Guida alle Wildcard

### 🔤 Wildcard Disponibili

| Simbolo | Significato | Esempio | Trova |
|---------|-------------|---------|-------|
| `*` | Qualsiasi carattere | `c*sa` | casa, cosa, cura... |
| `@` | Vocale (a,e,i,o,u) | `c@sa` | casa, cosa (no cura) |
| `#` | Consonante | `#@sa` | casa, masa, pasa... |
| `-` | Sottostringa | `-tro` | metro, altro, contro... |

### 📏 Filtri di Lunghezza (Sottostringhe)

| Operatore | Significato | Esempio | Trova |
|-----------|-------------|---------|-------|
| `=N` | Esatta lunghezza | `-tro=5` | metro, altro (5 lettere) |
| `<N` | Meno di N lettere | `-mente<8` | mente (5), demente (7) |
| `>N` | Più di N lettere | `-zione>10` | informazione, costituzione... |

## 💡 Esempi Pratici

### Pattern Comuni per Cruciverba

```python
# Parole di 4 lettere: c + qualsiasi + qualsiasi + a
cerca_in_tutti_dizionari(dizionari, 'c**a')

# Parole: consonante + vocale + s + a (casa, masa...)
cerca_in_tutti_dizionari(dizionari, '#@sa')

# Parole di 5 lettere con vocali in 2ª e 4ª posizione
cerca_in_tutti_dizionari(dizionari, '*@*@*')

# Parole che finiscono in "-zione" di qualsiasi lunghezza
cerca_in_tutti_dizionari(dizionari, '***zione')
```

### Ricerca per Sottostringhe

```python
# Tutte le parole che contengono "tro"
cerca_in_tutti_dizionari(dizionari, '-tro')

# Solo parole di 5 lettere che contengono "tro"
cerca_in_tutti_dizionari(dizionari, '-tro=5')

# Parole lunghe (>8 lettere) che contengono "zione"
cerca_in_tutti_dizionari(dizionari, '-zione>8')

# Parole corte (<10 lettere) che contengono "mente"
cerca_in_tutti_dizionari(dizionari, '-mente<10')
```

### Output Esempio
```
🔍 Ricerca sottostringa: 'tro' con filtro lunghezza '=5'
============================================================

📚 ITA: 12 risultati
   1. altro
   2. metro
   3. intro
   ...

📚 ENG: 8 risultati
   1. intro
   2. retro
   ...

============================================================
📊 TOTALE: 20 parole trovate in 2 dizionari
```

## 📁 Struttura del Progetto

```
dizionario/
├── README.md                 # Questa guida
├── ricerca_parole.ipynb     # Notebook principale Jupyter
├── .gitignore               # Esclude file dizionario
└── dizionari/               # ⚠️ AGGIUNGI I TUOI DIZIONARI QUI
    ├── italiano.txt         # Una parola per riga
    ├── inglese.txt          # Encoding UTF-8
    └── altri_dizionari.txt  # Nomi a piacere
```

## 📚 Dizionari

### ⚠️ Importante: File Dizionario Non Inclusi

I file dizionario **non sono inclusi** nel repository per rispettare i diritti d'autore. Devi aggiungere i tuoi file!

### Come Aggiungere Dizionari

1. **Crea la cartella**: `mkdir dizionari` (se non esiste)
2. **Scarica dizionari** da fonti legittime (vedi [Fonti Consigliate](#fonti-consigliate))
3. **Formato richiesto**: File `.txt` con una parola per riga
4. **Encoding**: Salva in UTF-8
5. **Nomi file**: Usa nomi descrittivi (es: `italiano.txt`, `inglese.txt`)

### Fonti Consigliate

- **Italiano**: [github.com/napolux/paroleitaliane](https://github.com/napolux/paroleitaliane)
- **Inglese**: [github.com/dwyl/english-words](https://github.com/dwyl/english-words)
- **Accademici**: Risorse universitarie con licenze aperte

Il sistema caricherà **automaticamente** tutti i file `.txt` trovati nella cartella `dizionari/`!

## 🎯 Casi d'Uso

### ✏️ Creazione Cruciverba
- Trova parole che si incastrino perfettamente negli spazi
- Testa diverse combinazioni di lunghezza
- Esplora terminazioni comuni (`-zione`, `-mente`, `-ando`)

### 🧩 Risoluzione Cruciverba  
- Inserisci le lettere note con pattern fissi (`c*s*`)
- Usa wildcard per lettere mancanti (`#@ro`)
- Cerca sottostringhe per parole parziali (`-tro`)

### 📝 Giochi di Parole
- Trova famiglie di parole (`-mente`, `-zione`)
- Parole con schemi specifici (`#@#@#`)
- Sfide linguistiche creative

## 🔧 Funzioni Principali

### `carica_tutti_dizionari()`
Carica automaticamente tutti i file `.txt` disponibili dalla cartella `dizionari/`.

### `cerca_in_tutti_dizionari(dizionari, pattern)`
Cerca un pattern in tutti i dizionari caricati. Supporta sia pattern fissi che sottostringhe.

**Parametri opzionali:**
- `mostra_tutti=False` - Limita l'output
- `max_risultati_per_dizionario=10` - Massimo risultati per dizionario

### `cerca_parole(dizionario, pattern)`
Cerca un pattern in un singolo dizionario specifico.

### `cerca_sottostringa(dizionario, testo, filtro_lunghezza)`
Cerca sottostringhe con filtri di lunghezza opzionali.

## 🌟 Caratteristiche Avanzate

- **Case Insensitive**: Funziona con maiuscole e minuscole
- **Rimozione Duplicati**: Elimina automaticamente parole duplicate
- **Gestione Errori**: Continua a funzionare anche con file corrotti
- **Statistiche Dettagliate**: Contatori e report per ogni ricerca
- **Scalabile**: Gestisce facilmente migliaia di parole

## 🛠️ Risoluzione Problemi

### "Nessun dizionario trovato"
- ✅ Verifica che i file `.txt` siano nella cartella `dizionari/`
- ✅ Controlla che i file abbiano estensione `.txt`
- ✅ Assicurati che ci sia almeno una parola per file

### "Encoding error"
- ✅ Salva i file dizionario in **UTF-8**
- ✅ Evita caratteri speciali non standard
- ✅ Una parola per riga, senza spazi extra

### Performance lenta
- ✅ Usa `mostra_tutti=False` per limitare l'output
- ✅ Aggiungi `max_risultati_per_dizionario=20`
- ✅ Usa pattern più specifici invece di troppe wildcard

## 🤖 AI Disclaimer

Questo progetto è stato sviluppato con l'assistenza di **AI generativa** per:
- Generazione e ottimizzazione del codice Python
- Documentazione e guide utente
- Testing e debugging

Il codice è stato **verificato manualmente** e funziona indipendentemente dall'assistenza AI. Tuttavia, l'autore **non** si assume la responsabilità per funzionalità e manutenzione.

## 👨‍💻 Contributori

Sviluppato per semplificare la creazione e risoluzione di cruciverba utilizzando Python e Jupyter Notebook.

**Buon divertimento con i tuoi cruciverba! 🧩✨**
