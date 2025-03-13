# Esercizio su PowerQuery (Injestion e normalizzazione dei dati)
## 📌 1. Importare il dataset in Power Query

### **In Excel:**
1. Apri **Excel** e vai su **Dati** → **Ottieni dati** → **Da file** → **Da cartella di lavoro o CSV**.  
2. Seleziona il file `.csv` e clicca su **Trasforma dati** per aprire Power Query.  

### **In Power BI:**
1. Apri **Power BI** e vai su **Home** → **Trasforma dati**.  
2. Seleziona **Ottieni dati** → **Da CSV** (o **Da Excel** se il file è in formato `.xlsx`).  

---

## 📌 2. Controllare e pulire i dati

### **Verificare il tipo di dati**
1. In **Power Query**, controlla la riga superiore della tabella.
2. Se una colonna è in formato **Testo** ma dovrebbe essere **Numero** o **Data**, clicca sull’icona del tipo di dato e cambia in:
   - **Numero intero** per quantità intere
   - **Numero decimale** per valori con virgola
   - **Data** per le date
   - **Testo** per descrizioni o nomi

### **Gestire valori mancanti**
1. Se ci sono celle vuote:
   - **Sostituire con un valore specifico**: Seleziona la colonna → Vai su **Trasforma** → **Sostituisci valori**.
   - **Rimuovere righe con dati mancanti**: Vai su **Riduci righe** → **Rimuovi righe** → **Rimuovi righe con valori nulli**.

### **Rinominare colonne**
1. Clicca sul nome della colonna e rinominala per maggiore chiarezza.

### **Eliminare colonne inutili**
1. Seleziona le colonne che non servono → **Rimuovi colonne**.

---

## 📌 3. Trasformare i dati

### **Filtrare i dati per anno e specie**
1. Seleziona la colonna **Anno** → Usa il filtro per mostrare solo il 2015.  
2. Seleziona la colonna **Specie Vegetale** → Filtra per **Melo**.  

### **Creare una colonna calcolata**
Ad esempio, per calcolare il **totale di lavoro (dipendente + familiare)**:  
1. Vai su **Aggiungi colonna** → **Colonna personalizzata**.  
2. Inserisci la formula:
   ```powerquery
   [lavoro_dipendente_ore_uomo] + [lavoro_famigliare_ore_uomo]
   ```
3. Clicca **OK** per creare la nuova colonna.

### **Raggruppare dati per Regione**
1. Seleziona la colonna **Regione**.  
2. Vai su **Trasforma** → **Raggruppa per**.  
3. Seleziona **Somma** per la colonna **Produzione**.  
4. Conferma per ottenere la produzione totale per ogni regione.

---

## 📌 4. Esplorare e visualizzare i dati

### **Ordinare i dati**
1. Seleziona la colonna **Produzione**.  
2. Clicca su **Ordinamento decrescente** per vedere le regioni con più produzione.  

### **Aggiungere una colonna condizionale**
Ad esempio, per classificare la produzione in **Alta, Media o Bassa**:  
1. Vai su **Aggiungi colonna** → **Colonna condizionale**.  
2. Imposta le regole:  
   - **Se Produzione > 10000, allora "Alta"**  
   - **Se Produzione > 5000, allora "Media"**  
   - **Altrimenti "Bassa"**  

---

## 📌 5. Salvare e applicare i dati

### **In Excel**
1. Clicca su **Chiudi e carica** per riportare i dati in un foglio Excel.  

### **In Power BI**
1. Clicca su **Chiudi e applica** per usare i dati nei report.  
