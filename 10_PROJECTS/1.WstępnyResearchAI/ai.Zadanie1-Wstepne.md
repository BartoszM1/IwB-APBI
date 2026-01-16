Poniżej znajduje się przykładowy opis **Zadania 1: Produkcja batonów czekoladowych**, przygotowany na podstawie dostarczonego szablonu oraz wytycznych z instrukcji projektowej.

---

# RAPORT: Transformacja Cyfrowa Linii Produkcyjnej Batonów (Zadanie 1)

## 1. Kontekst Biznesowy i Operacyjny

* **Wprowadzenie do Domeny:** Produkcja opiera się na przetwarzaniu masy czekoladowej (płynu nienewtonowskiego), co wymaga precyzyjnej kontroli procesów krystalizacji tłuszczu (temperowanie).
* 
**Wyzwania Technologiczne:** Obecnie występuje brak korelacji danych między halą produkcyjną a systemem biurowym (ERP), co uniemożliwia szybkie śledzenie partii surowców (kakao) w gotowym produkcie.


* **Model AS-IS:** Kontrola procesów odbywa się wyspowo, a raportowanie jakościowe i genealogia partii bazują na zapisach papierowych, co generuje opóźnienia w przypadku audytów.

## 2. Cele Strategiczne i Wskaźniki Sukcesu (KPI)

| Cel Biznesowy | Wartość Docelowa (Target) | Uzasadnienie |
| --- | --- | --- |
| **Wydajność Operacyjna** | +15% wzrost OEE | Optymalizacja planowania zleceń przez integrację MES z ERP.

 |
| **Redukcja Przestojów** | -20% nieplanowany Downtime | Szybsza reakcja serwisu dzięki monitorowaniu parametrów pracy maszyn w czasie rzeczywistym.

 |
| **Traceability** | < 2 minuty na raport | Pełna genealogia partii (kakao → pakowanie) dostępna natychmiastowo.

 |

---

## 3. Architektura Biznesowa (Warstwa Biznesowa)

### 3.1. Zakres Procesów (BPMN)

W ramach projektu zamodelowano dwa kluczowe procesy w notacji BPMN na poziomie szczegółowości N-2:

* 
**Proces 1: Order-to-Batch:** Obejmuje kroki od planowania zlecenia, przez przydział surowców, wykonanie receptury, kontrolę parametrów (temperatura/lepkość), aż po pakowanie.


* 
**Proces 2: Batch Traceability Request:** Proces obsługi zapytania o historię partii, konsolidujący dane z MES, ERP i LIMS dla klienta lub inspekcji.



### 3.2. Analiza Interesariuszy

* 
**Planista:** Odpowiada za proces "Order-to-Batch" i przydział zasobów.


* 
**QA (Kontrola Jakości):** Realizuje usługę "Produkty w jakości zgodnej z recepturą" oraz weryfikuje raporty traceability.


* 
**Mistrz Zmiany / Maintenance:** Monitoruje ciągłość pracy linii i zgłasza niezgodności (CAPA).



---

## 4. Architektura Aplikacji (Warstwa Aplikacyjna)

Systemy zostały zintegrowane w celu zapewnienia "jednej prawdy o danych":

* 
**ERP:** Obsługuje funkcje planowania, zakupów oraz zarządzania danymi podstawowymi (BOM).


* 
**MES:** Kluczowe narzędzie do zarządzania egzekucją produkcji, realizujące usługi "Recepturowanie" oraz "Genealogia partii".


* 
**LIMS/QA:** System zarządzania informacją laboratoryjną, wspierający kontrolę parametrów jakościowych.


* 
**SCADA/HMI:** Zapewnia wizualizację procesów fizycznych na hali.



---

## 5. Architektura Technologiczna (Warstwa Infrastruktury)

Zgodnie z wymaganiami technicznymi, zastosowano następujące relacje :

* 
**Węzły i Urządzenia:** Urządzenia takie jak PLC, czujniki temperatury i wagi są przypisane (**Assignment**) do węzła Edge Gateway.


* 
**Oprogramowanie systemowe:** Na węzłach (Serwer MES/ERP) zainstalowano oprogramowanie (np. Linux, SQL DB, OPC-UA Server).


* **Usługi technologiczne:**
* Urządzenia realizują (**Realization**) usługę "Monitoring linii".


* Oprogramowanie systemowe realizuje (**Realization**) usługi "Integracja OPC-UA" oraz "ETL do ERP".




* 
**Artefakty:** Logi produkcyjne i raporty QA są przypisane (**Assignment**) do odpowiednich węzłów serwerowych.



---

## 6. Motywacja, Wymagania i Pryncypia

* 
**Pryncypium:** "Jedna prawda o danych jakościowych" – dane z MES są nadrzędne wobec manualnych logów.


* 
**Wymagania:** Zapewnienie dostępności systemu MES na poziomie SLA 99.9% oraz obsługa etykietowania alergenów.


* 
**Cel:** Automatyczna korelacja danych (kakao → partia gotowa) w czasie poniżej 2 minut.



---

## 7. Analiza Luk i Plan Migracji

* 
**Analiza Luk:** Zidentyfikowano brak automatycznego przesyłu danych z wag do systemu ERP (luka technologiczna) oraz konieczność wycofania papierowych kart partii.


* **Plan Migracji (Kodowanie kolorami):**
* 
**Zielony (Nowe):** Moduł genealogii w MES, bramki Edge Gateway.


* 
**Niebieski (Modyfikacja):** Interfejsy w systemie ERP do odbioru danych z produkcji.


* 
**Czerwony (Usunięcie):** Ręczne formularze ewidencji produkcji.





---

## 8. Zarządzanie Ryzykiem i Zgodność

* 
**Ryzyka:** Możliwe przestoje systemu SCADA/MES mogą wstrzymać produkcję (mitygacja: klaster wysokiej dostępności HA).


* 
**Zgodność:** System musi spełniać wymogi etykietowania alergenów oraz standardy bezpieczeństwa żywności (HACCP).


* 
**Metryki:** Monitorowanie OEE, średniego czasu odpowiedzi traceability oraz liczby niezgodności na 1000 partii.



---

**Następny krok:** Czy chciałbyś, abym przygotował teraz podobny zarys dla Zadania 2, dotyczącego produkcji lotniczej i cyfrowego bliźniaka?
