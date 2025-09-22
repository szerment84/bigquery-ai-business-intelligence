README
🇬🇧 English description
BigQuery AI — Building the Future of Data Analysis

This Jupyter notebook demonstrates how to leverage BigQuery AI and generative functions in SQL and Python to build intelligent business applications and workflows.

Features:

Usage of built-in BigQuery AI functions (ML.GENERATE_TEXT, AI.GENERATE, AI.FORECAST, etc.).

Climate, business, and ROI analysis directly in BigQuery.

Practical use cases: forecasting, reporting, risk evaluation, and ROI estimation.

Step-by-step execution with clearly separated notebook cells.

How to use:

Open the .ipynb file in Kaggle Notebooks or Google Colab.

Configure Google Cloud Vertex AI connection in BigQuery.

Select a model available in Vertex AI (e.g., Gemini).

Generate and upload your service account JSON key for authentication in the notebook.

Run each cell step by step and adjust input parameters as needed.

Business applications:

Prioritizing investments and locations.

Automated KPI reporting.

Forecasting market and climate impacts.

Building intelligent dashboards in BigQuery.

🔧 Section 2 — User Parameters (Python)

In the notebook, users must provide specific parameters to customize the analysis:

# Location parameters
country_code = 'PL'          # ISO country code
city_name = 'Kraków'         # City name (ASCII characters recommended)
since_year = 2015            # Start year for analysis

# BigQuery connection
conn = 'us.vertex_ai_connection'   # Vertex AI connection

# Business ROI parameters
cost_per_hour_pln = 1800.0        # Downtime cost per hour [PLN]
hours_lost_per_heat_day = 2.0     # Hours lost per extreme heat day
productivity_drop_pct = 0.08      # Productivity decrease during heat (%)
capex_adaptation_pln = 120000.0   # CAPEX for adaptation [PLN]
opex_year_pln = 12000.0           # Annual OPEX for adaptation [PLN]
amort_years = 5                   # Investment amortization period [years]


These parameters are editable by the user and directly affect ROI and climate risk calculations.

🇵🇱 Opis projektu
BigQuery AI — Budowanie przyszłości analizy danych

Ten notatnik Jupyter pokazuje, jak wykorzystać BigQuery AI oraz funkcje generatywne w SQL i Pythonie do budowania inteligentnych aplikacji biznesowych i przepływów pracy.

Funkcjonalności:

Wykorzystanie wbudowanych funkcji BigQuery AI (ML.GENERATE_TEXT, AI.GENERATE, AI.FORECAST).

Analiza klimatyczna, biznesowa i ROI bezpośrednio w BigQuery.

Praktyczne przykłady: prognozowanie, raportowanie, ocena ryzyka i ROI.

Kod podzielony na osobne komórki dla łatwiejszego śledzenia.

Jak uruchomić:

Otwórz plik .ipynb w Kaggle Notebooks lub Google Colab.

Skonfiguruj połączenie z Google Cloud Vertex AI w BigQuery.

Wybierz odpowiedni model (np. Gemini).

Wygeneruj i załaduj plik JSON z kluczem konta serwisowego do autoryzacji w notatniku.

Uruchamiaj kolejne komórki krok po kroku i modyfikuj parametry wejściowe.

Zastosowania biznesowe:

Priorytetyzacja inwestycji i lokalizacji biznesowych.

Automatyczne raportowanie KPI.

Prognozowanie trendów klimatycznych i biznesowych.

Tworzenie inteligentnych dashboardów opartych o BigQuery.

🔧 Sekcja 2 — Parametry użytkownika (Python)

W notatniku znajduje się sekcja, w której użytkownik wprowadza swoje dane wejściowe. To one determinują wynik analizy:

# Parametry lokalizacji
country_code = 'PL'          # Kod kraju ISO
city_name = 'Kraków'         # Nazwa miasta (lepiej bez znaków diakrytycznych)
since_year = 2015            # Rok początkowy analizy

# Połączenie do Vertex AI
conn = 'us.vertex_ai_connection'   # Połączenie z Vertex AI w BigQuery

# Parametry biznesowe (ROI)
cost_per_hour_pln = 1800.0        # Koszt godziny przestoju [PLN]
hours_lost_per_heat_day = 2.0     # Liczba godzin straconych w dniu upału
productivity_drop_pct = 0.08      # Spadek wydajności (%) w czasie upałów
capex_adaptation_pln = 120000.0   # CAPEX adaptacji klimatycznej [PLN]
opex_year_pln = 12000.0           # Roczny OPEX adaptacji [PLN]
amort_years = 5                   # Okres amortyzacji inwestycji [lata]


➡️ Ta sekcja pozwala użytkownikowi dostosować analizę do własnej lokalizacji, kosztów i założeń biznesowych.
