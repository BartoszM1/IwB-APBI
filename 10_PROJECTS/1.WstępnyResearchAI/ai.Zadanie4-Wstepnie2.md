Poniżej znajduje się raport dla **Zadania 4: Badania kliniczne nowego kosmetyku**, opracowany na podstawie dostarczonych specyfikacji, plików BPMN oraz założeń projektowych.

---

# RAPORT: Transformacja Cyfrowa Procesu Badań Klinicznych (Zadanie 4)

## 1. Kontekst Biznesowy i Operacyjny

* **Wprowadzenie do Domeny:** Badania kliniczne produktów kosmetycznych wymagają rygorystycznego przestrzegania zasad Dobrej Praktyki Klinicznej (GCP).
* **Wyzwania Technologiczne:** Kluczowym problemem jest zapewnienie 100% rejestracji zdarzeń niepożądanych (AE) oraz skrócenie czasu rekrutacji uczestników.
* **Model AS-IS:** Obecne procesy opierają się na manualnym zbieraniu zgód (papier), co utrudnia zachowanie pełnego śladu rewizyjnego (audit trail) i wydłuża etap screeningu.

## 2. Cele Strategiczne i Wskaźniki Sukcesu (KPI)

| Cel Biznesowy | Wartość Docelowa (Target) | Uzasadnienie |
| --- | --- | --- |
| **Skrócenie rekrutacji** | -20% czasu | Automatyzacja screeningu i wdrożenie e-rekrutacji. |
| **Rejestracja AE/SAE** | 100% kompletności | Wykorzystanie aplikacji ePRO do bezpośredniego raportowania przez pacjenta. |
| **Zgodność GCP** | Pełna zgodność | Wdrożenie elektronicznej zgody (eConsent) z pełnym audit trail. |

---

## 3. Architektura Biznesowa (Warstwa Biznesowa)

### 3.1. Zakres Procesów (BPMN)

Zgodnie z wymaganiami zamodelowano procesy na poziomie szczegółowości N-2:

* **Proces 1: Screening & Enrollment:**
* 
**Pre-screening:** Wstępna weryfikacja kryteriów włączenia i wyłączenia przez koordynatora.


* 
**eConsent:** Podpisanie zgody przez uczestnika na tablecie klinicznym.


* 
**Wizyta Baseline:** Pełne badanie lekarskie i wprowadzenie danych do systemu EDC.


* 
**Randomizacja i Alokacja:** Automatyczny przydział do grupy badawczej i wyznaczenie numeru zestawu (Kit ID) przez silnik IRT.




* **Proces 2: AE/SAE Reporting & Safety:**
* 
**Zgłaszanie objawów:** Pacjent raportuje AE w aplikacji ePRO (w domu) lub podczas wizyty w ośrodku.


* 
**Triaging:** Główny badacz (PI) ocenia związek przyczynowy z badaniem.


* 
**Ocena ciężkości (SAE):** Jeśli zdarzenie jest poważne (zagrożenie życia/hospitalizacja), następuje automatyczna notyfikacja sponsora i komisji bioetycznej.


* 
**Finalizacja:** Kodowanie MedDRA w eCRF i zamknięcie zdarzenia po osiągnięciu rezultatu (outcome).





### 3.2. Analiza Interesariuszy

* **Główny badacz (PI) i Koordynator:** Nadzór nad screeningiem, wizytami baseline i oceną medyczną zdarzeń.
* **Uczestnik (Pacjent):** Odpowiada za podpisanie eConsent oraz raportowanie ePRO.
* **Sponsor i Safety Team:** Monitorowanie bezpieczeństwa i odbiór alertów SAE w czasie rzeczywistym.

---

## 4. Architektura Aplikacji (Warstwa Aplikacyjna)

Systemy wspierają cyfrowy obieg danych klinicznych:

* **eCRF/EDC:** System zbierania danych klinicznych i kart obserwacji.
* **Silnik IRT:** Moduł randomizacji i automatycznej alokacji materiałów badawczych.
* **ePRO i eConsent:** Aplikacje mobilne dla uczestników do zdalnego raportowania i podpisów.
* **CTMS:** System zarządzania całym badaniem klinicznym.

---

## 5. Architektura Technologiczna (Warstwa Infrastruktury)

* **Węzły:** Serwery EDC, CTMS oraz IRT hostujące kluczowe aplikacje badawcze.
* **Urządzenia:** Urządzenia mobilne uczestników oraz serwery podpisu elektronicznego realizujące usługę „Secure eConsent”.
* **Usługi technologiczne:** Silniki bazy danych realizujące usługę „Audit & Monitoring”.
* **Artefakty:** Karty eCRF, logi randomizacji oraz raporty AE przypisane do odpowiednich węzłów.

---

## 6. Motywacja, Wymagania i Pryncypia

* **Pryncypium:** „Jedno źródło danych trial master file” – całkowita eliminacja papieru i duplikacji danych.
* **Wymagania:** Zapewnienie pełnej zgodności z GCP poprzez audit trail dla elektronicznych zgód.
* **Cel operacyjny:** Skrócenie czasu zamknięcia bazy danych (data lock) po zakończeniu wizyt.

---

## 7. Analiza Luk i Plan Migracji

* **Analiza Luk:** Brak modułu eConsent w obecnej architekturze, co uniemożliwia cyfrowy screening.
* **Plan Migracji:**
* **Zielony (Nowe):** Wdrożenie modułu eConsent oraz systemu IRT do randomizacji.
* **Niebieski (Modyfikacja):** Rozszerzenie EDC o funkcjonalność raportowania AE zintegrowanego z ePRO.
* **Czerwony (Usunięcie):** Wycofanie papierowych kart wizyt i manualnych list randomizacyjnych.



---

## 8. Zarządzanie Ryzykiem i Zgodność

* **Ryzyka:** Ryzyko niekompletności danych AE (mitygowane przez ePRO) oraz wyciek danych osobowych (mitygowany przez Secure eConsent).
* **Zgodność:** Pełna zgodność z GCP oraz lokalnymi regulacjami ochrony danych uczestników badań.
* **Metryki:** Czas rekrutacji, kompletność raportów AE oraz czas do data lock.

---

**Następny krok:** Czy chciałbyś, abym przygotował teraz „Mapę impaktu zmiany”, która łączy cele biznesowe z infrastrukturą technologiczną dla wybranego zadania?
