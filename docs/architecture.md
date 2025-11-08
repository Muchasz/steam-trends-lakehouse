## Warstwy danych

### Bronze (Raw Layer)
- Zawiera surowe dane pobrane z API, plików lub źródeł transakcyjnych.
- Format: CSV, JSON, Parquet (bez modyfikacji).
- Przechowywane w Azure Data Lake Storage Gen2 w ścieżkach np.:
  `abfss://datalake@storageaccount.dfs.core.windows.net/bronze/{source}/{date}/`
- Przykład: `/bronze/weather/2025-11-08/weather_raw_*.json`

### Silver (Cleaned Layer)
- Oczyszczone i znormalizowane dane z Bronze.
- Usunięte duplikaty, poprawione typy danych, walidacje.
- Format: Delta Lake (umożliwia updaty i wersjonowanie).
- Przechowywane w ADLS: `/silver/{domain}/{table}/`
- Przykład: `/silver/weather/weather_clean.delta`

### Gold (Analytics / Business Layer)
- Agregaty lub widoki pod raportowanie i BI.
- Dane gotowe do analizy przez Power BI / SQL / ML.
- Format: Delta lub Parquet.
- Przykład: `/gold/weather/avg_temp_by_city/`

## Przepływ danych (Data Flow)

1. **Ingestion (Extract)**
   - Skrypt w Pythonie lub pipeline ADF pobiera dane z API lub plików publicznych.
   - Dane trafiają do warstwy *bronze* w Azure Data Lake Gen2.

2. **Transformacje (Load/Transform)**
   - Notatniki Databricks (PySpark) odczytują dane z *bronze*,
     oczyszczają, standaryzują schemat i zapisują jako Delta w *silver*.

3. **Modelowanie / Agregacja (ELT)**
   - Za pomocą SQL lub dbt modele tworzą warstwę *gold*
     (np. agregaty dzienne, raporty).

4. **Prezentacja / Analiza**
   - Power BI, Streamlit lub Databricks SQL wykorzystują dane z *gold*.