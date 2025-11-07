# Project Idea: Steam Game Trends Lakehouse

## 1. Opis projektu
Celem projektu jest zbudowanie potoku danych (ETL/ELT), który analizuje trendy popularności gier na platformie **Steam** w zależności od czynników takich jak cena, data premiery i sezonowość.

Projekt służy jako praktyczne ćwiczenie z zakresu **Data Engineeringu** — od pobierania danych (ingestion), przez przetwarzanie i modelowanie, aż po analizę i wizualizację wyników.

## 2. Źródła danych
- **SteamCharts** – dane o liczbie aktywnych graczy w czasie  
  ↳ https://steamcharts.com  
  *(pobierane przez scraper lub zapytania HTTP do stron poszczególnych gier)*  
- **Steam API** – dane o grach (tytuł, cena, developer, data premiery, itp.)  
  ↳ https://developer.valvesoftware.com/wiki/Steam_Web_API  

Dane te zostaną połączone i przetwarzane w ramach architektury lakehouse.

## 3. Cele techniczne
- Zbudować warstwy **bronze / silver / gold** w oparciu o **Azure Data Lake Gen2** i **Databricks Delta Lake**.  
- Użyć **PySpark** do przetwarzania i łączenia danych z różnych źródeł.  
- Dodać testy jakości danych (np. Great Expectations / dbt tests).  
- Zautomatyzować potok za pomocą **Databricks Workflows** lub **Azure Data Factory**.  
- Wizualizować dane w **Power BI / Streamlit**.

## 4. Główne pytania analityczne
- Jak zmienia się liczba aktywnych graczy w czasie dla topowych gier?
- Czy istnieje korelacja między zmianą ceny gry a wzrostem/ spadkiem aktywności graczy?
- Które gatunki gier wykazują największe wzrosty sezonowe?

## 5. Stack technologiczny
| Warstwa | Technologia |
|----------|--------------|
| Storage | Azure Data Lake Gen2 |
| Compute | Databricks (PySpark, SQL) |
| Orkiestracja | Databricks Workflows / Azure Data Factory |
| Jakość danych | dbt, Great Expectations |
| IaC | Terraform |
| Wizualizacja | Power BI / Streamlit |

## 6. Następne kroki
- [x] Wybór źródeł danych  
- [ ] Stworzenie repo i struktury projektu  
- [ ] Przygotowanie sample dataset i ingestion stub  
- [ ] Zaprojektowanie architektury Lakehouse  
- [ ] Rozpoczęcie implementacji (Week 2)

---