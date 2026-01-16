Poniżej znajduje się przykładowy opis **Zadania 4: Badania kliniczne nowego kosmetyku**, opracowany na podstawie dostarczonego szablonu oraz szczegółowych wytycznych projektowych dotyczących standardów GCP i eCRF.

---

# RAPORT: Transformacja Cyfrowa Procesu Badań Klinicznych (Zadanie 4)

## 1. Kontekst Biznesowy i Operacyjny

* 
**Wprowadzenie do Domeny:** Badania kliniczne kosmetyków wymagają ścisłego przestrzegania zasad Dobrej Praktyki Klinicznej (GCP).


* 
**Wyzwania Technologiczne:** Głównym problemem jest zapewnienie 100% rejestracji zdarzeń niepożądanych (AE) oraz skrócenie czasu rekrutacji uczestników.


* 
**Model AS-IS:** Obecne procesy często opierają się na manualnym zbieraniu zgód, co utrudnia zachowanie pełnego śladu rewizyjnego (audit trail) i wydłuża etap screeningu.



## 2. Cele Strategiczne i Wskaźniki Sukcesu (KPI)

| Cel Biznesowy | Wartość Docelowa (Target) | Uzasadnienie |
| --- | --- | --- |
| **Skrócenie rekrutacji** | -20% czasu 

 | Automatyzacja screeningu i e-rekrutacji.

 |
| **Rejestracja AE/SAE** | 100% kompletności 

 | Wykorzystanie ePRO do bezpośredniego raportowania przez pacjenta.

 |
| **Zgodność GCP** | Pełna zgodność 

 | Wdrożenie elektronicznej zgody (eConsent) z audit trail.

 |

---

## 3. Architektura Biznesowa (Warstwa Biznesowa)

### 3.1. Zakres Procesów (BPMN)

W ramach zadania zamodelowano procesy na poziomie szczegółowości N-2:

* 
**Proces 1: Screening & enrollment:** Obejmuje kroki od pre-screeningu, przez eConsent, randomizację, wizytę baseline, aż po alokację materiałów badawczych.


* 
**Proces 2: AE/SAE reporting:** Proces zgłaszania zdarzeń niepożądanych, obejmujący triaging, ocenę ciężkości, notyfikację sponsora oraz zamknięcie wpisu w eCRF.



### 3.2. Analiza Interesariuszy

* 
**Główny badacz (PI) i Koordynator:** Odpowiadają za screening i bezpośredni nadzór nad uczestnikami.


* 
**Sponsor i Monitor:** Weryfikują dane w systemie eCRF i dbają o jakość badania.


* 
**Uczestnik:** Wykorzystuje urządzenia mobilne do raportowania ePRO i udzielania zgody eConsent.



---

## 4. Architektura Aplikacji (Warstwa Aplikacyjna)

Zastosowane komponenty wspierają cyfrowy obieg danych klinicznych:

* 
**eCRF/EDC:** System do zbierania danych klinicznych i zarządzania kartami obserwacji.


* 
**Randomization/IRT:** Moduł odpowiedzialny za automatyczną alokację uczestników do grup badawczych.


* 
**ePRO i eConsent:** Aplikacje mobilne dla uczestników do zdalnego raportowania i podpisywania zgód.


* 
**CTMS:** System do zarządzania całym badaniem klinicznym (Clinical Trial Management System).



---

## 5. Architektura Technologiczna (Warstwa Infrastruktury)

Warstwa ta uwzględnia wymagane relacje technologiczne:

* 
**Węzły:** Serwery EDC, CTMS oraz IRT.


* 
**Urządzenia:** Urządzenia mobilne uczestników oraz serwery podpisu elektronicznego, realizujące usługę „Secure eConsent”.


* 
**Oprogramowanie systemowe:** Silniki baz danych i systemy wiadomości realizują usługę „Audit & Monitoring”.


* 
**Artefakty:** Do węzłów przypisane są obiekty takie jak „karta eCRF”, „log randomizacji” oraz „raport AE”.



---

## 6. Motywacja, Wymagania i Pryncypia

* 
**Pryncypium:** „Jedno źródło danych trial master file” – eliminacja duplikacji danych papierowych.


* 
**Wymagania:** Elektroniczna zgoda musi być zgodna z GCP i posiadać pełny audit trail.


* 
**Cel operacyjny:** Skrócenie czasu zamknięcia bazy danych (data lock) po zakończeniu wizyt.



---

## 7. Analiza Luk i Plan Migracji

* 
**Analiza Luk:** Zidentyfikowano brak modułu elektronicznej zgody (eConsent), co jest kluczową luką w obecnej architekturze.


* **Plan Migracji (Kodowanie kolorami):**
* 
**Zielony (Nowe):** Moduł eConsent oraz system IRT do randomizacji.


* 
**Niebieski (Modyfikacja):** Rozszerzenie systemu EDC o funkcjonalność raportowania AE.


* 
**Czerwony (Usunięcie):** Papierowe karty wizyt i manualne listy randomizacyjne.





---

## 8. Zarządzanie Ryzykiem i Zgodność

* 
**Ryzyka:** Brak kompletności danych o zdarzeniach niepożądanych (AE) oraz ryzyko wycieku danych osobowych uczestników.


* 
**Zgodność:** Zapewnienie pełnej zgodności z GCP oraz regulacjami dotyczącymi ochrony danych uczestników.


* 
**Metryki:** Średni czas rekrutacji, kompletność raportów AE oraz czas od ostatniej wizyty do zamknięcia danych (data lock).



---

**Możliwy następny krok:** Czy chciałbyś, abym przygotował teraz „Mapę impaktu zmiany”, która łączy cele biznesowe z infrastrukturą technologiczną dla jednego z powyższych zadań?
