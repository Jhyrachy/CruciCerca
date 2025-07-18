# 🧩 Crossword Solver - Tool per Cruciverba

Un potente strumento Python per **creare e risolvere cruciverba** utilizzando pattern avanzati e wildcard intelligenti.

## 🎯 Caratteristiche Principali

### ## �‍💻 Contributori

Creato per semplificare la creazione e risoluzione di cruciverba usando Python e Jupyter Notebook.

---

## 🤖 Disclaimer - AI Generativa

### Utilizzo di Intelligenza Artificiale

Questo progetto è stato sviluppato con l'assistenza di **AI generativa** (GitHub Copilot/ChatGPT/Claude) per:

- **Generazione del codice**: Le funzioni Python e la logica di ricerca
- **Documentazione**: README, commenti nel codice e guide utente
- **Ottimizzazione**: Miglioramento delle performance e della struttura
- **Testing**: Suggerimenti per casi di test e debugging

### Responsabilità e Trasparenza

- **Codice Verificato**: Tutto il codice è stato testato e validato manualmente
- **Logica Originale**: I requisiti e l'architettura sono stati definiti dall'autore umano
- **Personalizzazione**: Il codice è stato adattato e modificato per le esigenze specifiche
- **Manutenzione**: L'autore si assume la responsabilità per bug e aggiornamenti

### Note per gli Utilizzatori

- Il codice funziona come documentato, indipendentemente dall'assistenza AI
- Gli algoritmi di ricerca sono standard e ben consolidati
- L'AI ha accelerato lo sviluppo ma non compromette la qualità o funzionalità
- Il progetto può essere modificato e esteso seguendo le pratiche standard di programmazione

---

## 📚 Attributioncerca Avanzata con Wildcard**
- **`*`** = qualsiasi carattere
- **`@`** = vocale (a, e, i, o, u)  
- **`#`** = consonante (tutte le altre lettere)
- **`-testo`** = sottostringa (trova parole che contengono 'testo')

### 📚 **Multi-Dizionario Automatico**
- Caricamento automatico di tutti i file `.txt` dalla cartella `dizionari/`
- Supporto per più lingue contemporaneamente
- Risultati organizzati per dizionario

### 🎨 **Interface User-Friendly**
- Output colorato e organizzato con emoji
- Statistiche dettagliate
- Ricerca interattiva

## 🚀 Esempi di Utilizzo

### Pattern Comuni per Cruciverba

```python
# Parola di 4 lettere che inizia con 'c' e finisce con 'a'
cerca_in_tutti_dizionari(dizionari, 'c**a')

# Parola: consonante-vocale-s-a (casa, masa, pasa...)
cerca_in_tutti_dizionari(dizionari, '#@sa')

# Parole di 5 lettere con vocali in 2ª e 4ª posizione
cerca_in_tutti_dizionari(dizionari, '*@*@*')

# Parole che contengono 'tro' (qualsiasi lunghezza)
cerca_in_tutti_dizionari(dizionari, '-tro')

# Parole che contengono 'zione' (qualsiasi lunghezza)
cerca_in_tutti_dizionari(dizionari, '-zione')

# NUOVO! Filtri di lunghezza per sottostringhe:
# Parole che contengono 'tro' di esattamente 5 lettere
cerca_in_tutti_dizionari(dizionari, '-tro=5')

# Parole che contengono 'mente' di meno di 10 lettere
cerca_in_tutti_dizionari(dizionari, '-mente<10')

# Parole che contengono 'zione' di più di 8 lettere
cerca_in_tutti_dizionari(dizionari, '-zione>8')
```

### Output Esempio
```
🔍 Ricerca sottostringa: 'tro' (parole che contengono questa sequenza)
============================================================

📚 DIZIONARIO_ITA: 15 risultati
   1. altro
   2. metro
   3. contro
   4. centro
   5. elettro
   ... e altri 10 risultati

📚 DIZIONARIO_ENG: 8 risultati
   1. strong
   2. control
   3. destroy
   4. electron
   ... e altri 4 risultati

============================================================
📊 TOTALE: 23 parole trovate in 2 dizionari
```

## 📁 Struttura del Progetto

```
dizionario/
├── README.md                 # Questo file
├── ricerca_parole.ipynb     # Notebook principale
├── dizionari/               # Cartella con i dizionari
│   ├── dizionario_ita.txt   # Dizionario italiano
│   ├── dizionario_eng.txt   # Dizionario inglese
│   └── ...                  # Altri dizionari
└── readme.txt              # Note aggiuntive
```

## 🛠️ Setup e Installazione

### Requisiti
- Python 3.6+
- Jupyter Notebook
- Librerie standard: `os`, `glob`

### Utilizzo Rapido

1. **Apri il notebook**: `ricerca_parole.ipynb`

2. **Esegui le celle in ordine**:
   - Cella 3: Carica le funzioni di importazione
   - Cella 5: Carica le funzioni di ricerca
   - Cella 7: Carica automaticamente tutti i dizionari

3. **Inizia a cercare**:
   - Cella 8: Esempi predefiniti
   - Cella 10: Ricerca interattiva

### Aggiungere Nuovi Dizionari

**⚠️ Importante**: I file dizionario non sono inclusi nel repository.

Per utilizzare il tool, devi aggiungere i tuoi file dizionario:

1. **Crea la cartella**: `mkdir dizionari` (se non esiste già)
2. **Aggiungi file .txt**: Ogni file deve contenere una parola per riga
3. **Encoding UTF-8**: Assicurati che i file siano salvati in UTF-8
4. **Nomenclatura**: Usa nomi descrittivi (es: `dizionario_ita.txt`, `english_words.txt`)

Basta aggiungere file `.txt` nella cartella `dizionari/` e il sistema li caricherà automaticamente!

## 📖 Guida alle Wildcard

### 🔍 Wildcard Disponibili:

| Simbolo | Significato | Esempio | Risultato |
|---------|-------------|---------|-----------|
| `*` | Qualsiasi carattere | `c*sa` | casa, cosa, cura... |
| `@` | Vocale (a,e,i,o,u) | `c@sa` | casa, cosa |
| `#` | Consonante | `#@sa` | casa, masa, pasa |
| `-` | Sottostringa | `-tro` | metro, altro, contro... |
| `-X=N` | Sottostringa + lunghezza esatta | `-tro=5` | metro, altro (5 lettere) |
| `-X<N` | Sottostringa + lunghezza massima | `-mente<10` | mente, demente (< 10) |
| `-X>N` | Sottostringa + lunghezza minima | `-zione>8` | informazione, situazione (> 8) |

### Pattern Utili per Cruciverba

- **Parole corte**: `#@#` (3 lettere: consonante-vocale-consonante)
- **Terminazioni**: `****zione` (parole che finiscono in -zione)
- **Iniziali doppie**: `##***` (due consonanti iniziali)
- **Alternanza**: `#@#@#` (consonante-vocale alternata)
- **Sottostringhe**: `-tro` (qualsiasi parola contenente 'tro')

### 📏 Filtri di Lunghezza per Sottostringhe

I filtri di lunghezza ti permettono di limitare i risultati delle sottostringhe a parole di una specifica lunghezza:

**Operatori disponibili:**
- `=N` - Esattamente N lettere
- `<N` - Meno di N lettere  
- `>N` - Più di N lettere

**Esempi pratici:**
- `-tro=5` → Solo parole di 5 lettere con 'tro': metro, altro, intro
- `-mente<8` → Parole corte con 'mente': mente (5), demente (7)
- `-zione>10` → Parole lunghe con 'zione': informazione (12), situazione (10+)

**Utilità per cruciverba:**
- Trova parole che si incastrino in spazi specifici
- Filtra risultati troppo lunghi o troppi corti
- Ottimizza la ricerca per griglie di dimensioni precise

## 🎯 Casi d'Uso

### ✏️ **Creazione Cruciverba**
- Trova parole che si incastrino perfettamente
- Testa diverse combinazioni di lunghezza
- Esplora sinonimi e varianti

### 🧩 **Risoluzione Cruciverba**
- Inserisci le lettere che conosci con pattern fissi
- Usa wildcard per le lettere mancanti
- Cerca sottostringhe con `-testo` per parole parziali
- Confronta risultati da più dizionari

### 📝 **Giochi di Parole**
- Anagrammi con pattern
- Parole con schemi specifici
- Ricerca di famiglie di parole (es: `-zione`, `-mente`)
- Sfide linguistiche creative

## 🔧 Funzioni Principali

### `carica_tutti_dizionari()`
Carica automaticamente tutti i file `.txt` disponibili.

### `cerca_in_tutti_dizionari(dizionari, pattern)`
Cerca un pattern in tutti i dizionari e mostra risultati divisi.

### `cerca_parole(dizionario, pattern)`
Cerca un pattern in un dizionario specifico.

## 🌟 Caratteristiche Avanzate

- **Case Insensitive**: Funziona con maiuscole/minuscole
- **Rimozione Duplicati**: Elimina automaticamente parole duplicate
- **Gestione Errori**: Continua a funzionare anche con file corrotti
- **Statistiche**: Contatori e report dettagliati
- **Scalabilità**: Gestisce facilmente migliaia di parole

## 🎨 Personalizzazione

### Modifica Wildcard
Puoi facilmente aggiungere nuove wildcard modificando la funzione `cerca_parole()`:

```python
elif pat_char == '%':  # Nuova wildcard
    # Tua logica personalizzata
```

### Filtri Personalizzati
Aggiungi filtri per lunghezza, frequenza, categoria, ecc.

## 🐛 Risoluzione Problemi

### Dizionari Non Trovati
- Verifica che i file `.txt` siano nella cartella `dizionari/`
- Controlla l'encoding (deve essere UTF-8)
- Assicurati che ci sia una parola per riga

### Performance Lenta
- Riduci `max_risultati_per_dizionario`
- Usa pattern più specifici
- Considera di dividere dizionari molto grandi

## 📈 Sviluppi Futuri

- [ ] Interface grafica (GUI)
- [ ] Supporto per definizioni
- [ ] Export in formati cruciverba
- [ ] API web per integrazione
- [ ] Database più ampi
- [ ] Analisi frequenza parole

## 👨‍💻 Contributori

Creato per semplificare la creazione e risoluzione di cruciverba usando Python e Jupyter Notebook.

---

## � Attribution

### Dizionari e Fonti Dati

I dizionari utilizzati in questo progetto provengono dalle seguenti fonti:

- **Dizionario Italiano**: https://github.com/napolux/paroleitaliane
- **Dizionario Inglese**: https://github.com/dwyl/english-words

### Note sui Diritti d'Autore

- I file di dizionario non sono inclusi nel repository per rispettare i diritti d'autore
- Gli utenti devono procurarsi i propri file dizionario da fonti legittime
- Assicurarsi di rispettare le licenze e i termini d'uso delle fonti utilizzate

### Licenze Consigliate per Dizionari

- **Creative Commons**: Dizionari con licenza CC-BY o CC-BY-SA
- **Open Source**: Progetti come Hunspell, OpenTaal, o simili
- **Pubblico Dominio**: Dizionari storici fuori copyright
- **Accademico**: Risorse universitarie con licenze appropriate

---

## �📞 Supporto

Per domande, suggerimenti o bug reports, consulta il notebook `ricerca_parole.ipynb` che contiene esempi dettagliati e documentazione interattiva.

**Buon divertimento con i tuoi cruciverba! 🧩✨**
