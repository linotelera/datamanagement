# Guida Passo-Passo: Normalizzazione e Categorizzazione dei Dati con PowerQuery

## Introduzione
Questa guida illustra il processo di normalizzazione e categorizzazione dei dati utilizzando PowerQuery su un dataset CSV.

## Passaggi

### 1. Importazione del CSV via Web
Utilizziamo PowerQuery per importare il dataset direttamente da un webservice.

#### Codice M per importare il dataset
```m
let
    Source = Csv.Document(Web.Contents("https://github.com/linotelera/datamanagement/raw/refs/heads/main/injestion/dataset_merged_full_apple.CSV"),
        [Delimiter=";", Columns=36, Encoding=65001, QuoteStyle=QuoteStyle.None]),
    PromotedHeaders = Table.PromoteHeaders(Source, [PromoteAllScalars=true])
    
    // Aggiungi eventuali trasformazioni qui
in
    PromotedHeaders
```

### 2. Pulizia e Normalizzazione dei Dati
Dopo l'importazione, normalizziamo le colonne eliminando spazi bianchi e correggendo i tipi di dati.

1. **Rinominare le colonne per una maggiore chiarezza.**
2. **Convertire i tipi di dati** per numeri, date e testi.
3. **Eliminare i valori nulli** e trattare i dati mancanti.

### 3. Categorizzazione dei Dati
Creiamo nuove colonne per categorizzare i dati:

- **Classificazione per Regione:** Raggruppiamo le aziende per Regione.
- **Classificazione per Produzione:** Definiamo fasce di produzione in base ai valori di `Produzione`.

```m
let
    Source = PromotedHeaders,
    AddRegionCategory = Table.AddColumn(Source, "Categoria Regione", each if [Regione] in {"Toscana", "Marche", "Umbria"} then "Centro" else if [Regione] in {"Piemonte", "Lombardia"} then "Nord" else "Sud"),
    AddProductionCategory = Table.AddColumn(AddRegionCategory, "Categoria Produzione", each if [Produzione] > 5000 then "Alta" else if [Produzione] > 1000 then "Media" else "Bassa")

in
    AddProductionCategory
```

### 4. Esportazione dei Dati Puliti
Dopo la trasformazione, possiamo caricare i dati normalizzati in Excel o in un database.
