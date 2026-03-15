# WF_ICP_Persona: BioAge

**Data:** 2026-03-15  
**Projekt:** BioAge - Kalkulator Wieku Funkcjonalnego  
**Status:** Idea → MVP

---

## 📋 Wejścia

- **1-liner:** "Sprawdź czy Twoje serce jest młode - profesjonalny test sprawności funkcjonalnej z raportem do lekarza"
- **Etap:** Idea / MVP
- **Wstępne ICP:** Osoby 40-65 lat dbające o zdrowie + Trenerzy personalni/fizjoterapeuci

---

## 🎯 ICP Card (Karty Postaci)

### ICP A: "Anna Kowalska" - Osoba 40+ dbająca o zdrowie

| Atrybut | Opis |
|---------|------|
| **Wiek** | 45-60 lat |
| **Wykształcenie** | Średnie-wyższe |
| **Praca** | Pracownik biurowy, menedżer średniego szczebla |
| **Dochód** | 5000-12000 PLN netto |
| **Technologia** | Smartphone + laptop, nie-techniczna |
| **Zainteresowania** | Zdrowie, fitness (spacery, joga), rodzina |
| **Obawy** | Lęk przed starzeniem, choroby cywilizacyjne |

**Główny Job:** "Chcę obiektywnie ocenić swoją sprawność i wiedzieć czy moje serce jeszcze daje radę."

**Ból:** "Wszystko jest rozproszone - kroki w telefonie, waga w łazience, tętno na zegarku. Brak jednego spójnego obrazu."

**Trigger:** Roczne badania kontrolne, początek nowego roku, zadyszka przy schodach.

**Decision Criteria:**
- Wynik musi być zrozumiały bez wiedzy technicznej
- Raport do pokazania lekarzowi
- Możliwość śledzenia postępów

**KPI sukcesu:**
- Czas wykonania testu < 5 minut
- Wynik w formie jednej liczby + interpretacja

---

### ICP B: "Marek Fizjo" - Trener personalny / Fizjoterapeuta

| Atrybut | Opis |
|---------|------|
| **Wiek** | 28-45 lat |
| **Wykształcenie** | Studia kierunkowe (AWF, fizjoterapia) |
| **Praca** | Fizjoterapeuta / Trener personalny |
| **Dochód** | 6000-20000 PLN/mies (zależny od liczby klientów) |
| **Technologia** | Smartphone, laptop, tablet |
| **Klienci** | Głównie 40+, po kontuzjach, seniorzy |

**Główny Job:** "Szybko ocenić poziom sprawności nowego klienta bez skomplikowanych testów."

**Ból:** "Subiektywna ocena - klient może kłamać o swojej sprawności. Potrzebuję obiektywnych liczb."

**Trigger:** Nowy klient w portfolio, koniec miesiąca treningowego.

**Decision Criteria:**
- Szybki test (5 minut na pierwszej wizycie)
- Profesjonalny raport do pokazania klientowi
- Możliwość śledzenia postępów wielu klientów

**KPI sukcesu:**
- Czas wdrożenia < 10 minut
- Raport gotowy w 2 minuty po teście

---

## 📊 Problem Matrix

| # | Problem | Trigger | Value (szacunek) | Current Solution | Impact | Confidence | Ease | Priority |
|---|---------|---------|------------------|------------------|--------|------------|------|----------|
| 1 | Brak profesjonalnego raportu do lekarza | Wizyta lekarska | Oszczędność ~500 PLN wizyty specjalistycznej | Ręczne notatki | 9 | 7 | 8 | **504** |
| 2 | Rozproszone dane o sprawności | Chęć monitorowania | ~3h/mies szukania info | Endomondo, Apple Health, Excel | 8 | 8 | 7 | **448** |
| 3 | Niepewność "czy jestem normalny" | Początek roku | Wartość niemierzalna ale wysoka | Google, fora | 7 | 6 | 9 | **378** |
| 4 | Brak obiektywnej oceny klienta (dla trenerów) | Nowy klient | Retencja klienta = ~2000 PLN/mies | Wywiad ustny | 9 | 7 | 6 | **378** |
| 5 | Trudność w pokazaniu postępów | Koniec programu | Retencja = ~1500 PLN/mies | Zdjęcia przed/po | 8 | 6 | 7 | **336** |
| 6 | Wysokie ryzyko kontuzji u klientów | Nowy klient 55+ | Uniknięcie odszkodowania ~20000 PLN | Brak narzędzi | 7 | 5 | 5 | **175** |

**Priority = Impact × Confidence × Ease**

---

## 🔬 Kwantyfikacja Wartości

### ICP A (Osoby 40+)

| Wartość | Szacunek | Założenie |
|---------|----------|-----------|
| Oszczędność czasu | 3h/mies | Szukanie info o sprawności |
| Oszczędność kosztów | 500 PLN/rok | Unikanie niepotrzebnych wizyt |
| Wartość psychologiczna | Wysoka | Spokój o zdrowie |

### ICP B (Trenerzy)

| Wartość | Szacunek | Założenie |
|---------|----------|-----------|
| Retencja klienta | 1500-3000 PLN/mies | Lepsze raportowanie = dłuższa współpraca |
| Oszczędność czasu | 30 min/klient | Szybsza ocena |
| Uniknięcie kontuzji | 5000-20000 PLN/rok | Mniej roszczeń |

---

## 🧪 Suggested Experiments

### Eksperyment 1: Landing Page Test

| Element | Opis |
|---------|------|
| **Cel** | Test komunikacji i willingness to pay |
| **Hipoteza** | "Sprawdź czy Twoje serce jest młode" = wyższy CTR niż "kalkulator wieku funkcjonalnego" |
| **Metric** | CTR, Email sign-up rate |
| **Koszt** | Niska (page + ads) |
| **Czas** | 3 dni |

**Copy test:**
- Wariant A: "Kalkulator wieku biologicznego"
- Wariant B: "Sprawdź czy Twoje serce jest młode"
- Wariant C: "Test sprawności dla seniorów"

---

### Eksperyment 2: Pre-Order Survey

| Element | Opis |
|---------|------|
| **Cel** | Walidacja willingness to pay |
| **Metoda** | Email do 100 osób z landing page |
| **Pytanie** | "Czy zapłaciłbyś 9.99 PLN za profesjonalny raport PDF do lekarza?" |
| **Koszt** | Niska |
| **Czas** | 5 dni |

---

### Eksperyment 3: Wywiady z Fizjoterapeutami

| Element | Opis |
|---------|------|
| **Cel** | Potwierdzenie ICP B |
| **Metoda** | 10 rozmów / LinkedIn outreach |
| **Pytania** | Zgodnie z JTBD script |
| **Koszt** | Niska |
| **Czas** | 7 dni |

---

## ✅ Checklista Końcowa

- [x] 1-stronicowa karta ICP (2 profile)
- [x] 5 Job Snapshotów (z JTBD)
- [x] Problem Matrix z priorytetami
- [x] 3 propozycje szybkich eksperymentów
- [x] Kwantyfikacja wartości

---

## 📈 Następne Kroki

| Krok | Workflow | Kiedy |
|------|----------|-------|
| 1 | Build MVP | Po potwierdzeniu eksperymentu #2 |
| 2 | GTM Strategy | Po ICP confirmation |
| 3 | Competitor Audit | Opcjonalnie |

---

*ICP Persona completed: 2026-03-15*
