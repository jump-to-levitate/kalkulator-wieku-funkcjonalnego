# 02. Specyfikacja Funkcjonalna: BioAge

## Projekt Studencki - Kalkulator Wieku Funkcjonalnego

---

## 1. Przegląd Aplikacji

**BioAge** to Single Page Application (SPA), która oblicza wiek funkcjonalny użytkownika na podstawie serii testów sprawnościowych.

### 1.1 Cele Projektu (dla zaliczenia)
- Implementacja algorytmów przeliczających wyniki testów na wiek
- Wizualizacja danych w formie wykresów
- Zapis danych w LocalStorage
- Responsywny interfejs użytkownika

---

## 2. Lista Testów i Algorytmy

### 2.1 Test Flamingo (Unipedal Stance Test)

**Cel:** Ocena równowagi i układu nerwowego

**Instrukcja:**
- Stań na jednej nodze ( dowolna )
- Zamknij oczy
- Zmierz czas do utrzymania pozycji

**Dane wejściowe:**
- `flamingoTime` - czas w sekundach (0-120)

**Algorytm (uproszczony):**

```
function calculateFlamingoAge(seconds, gender):
    if gender == 'male':
        if seconds >= 30  return 20
        if seconds >= 25  return 25
        if seconds >= 20  return 30
        if seconds >= 15  return 40
        if seconds >= 10  return 50
        if seconds >= 5   return 65
        return 80
    else:  // female
        if seconds >= 28  return 20
        if seconds >= 23  return 25
        if seconds >= 18  return 30
        if seconds >= 13  return 40
        if seconds >= 8   return 50
        if seconds >= 4   return 65
        return 80
```

**Waga w średniej ważonej:** 15%

---

### 2.2 Test SRT (Sitting-Rising Test)

**Cel:** Ocena mobilności i siły dolnej części ciała

**Instrukcja:**
- Usiądź w pozycji skrzyżnej (na podłodze)
- Wstań bez użycia rąk
- Każde podparcie = -1 punkt

**Dane wejściowe:**
- `srtScore` - liczba punktów (0-10)

**Algorytm:**

```
function calculateSRTAge(score):
    if score >= 10  return 20
    if score >= 9   return 25
    if score >= 8   return 30
    if score >= 7   return 40
    if score >= 6   return 50
    if score >= 5   return 60
    if score >= 4   return 70
    if score >= 3   return 75
    return 85
```

**Waga w średniej ważonej:** 25%

---

### 2.3 Test Coopera (12-minutowy bieg)

**Cel:** Ocena wydolności krążeniowo-oddechowej

**Instrukcja:**
- Biegaj lub marsz przez 12 minut
- Zmierz pokonany dystans

**Dane wejściowe:**
- `cooperDistance` - dystans w metrach (0-5000)

**Obliczenia:**

```
// Wzór Coopera
vo2max = (distanceMeters - 504.9) / 44.73

// Klasyfikacja VO2max na wiek
function calculateCooperAge(vo2max, gender):
    if gender == 'male':
        if vo2max >= 55  return 20
        if vo2max >= 50  return 25
        if vo2max >= 45  return 30
        if vo2max >= 40  return 40
        if vo2max >= 35  return 50
        if vo2max >= 30  return 60
        if vo2max >= 25  return 70
        return 80
    else:  // female
        if vo2max >= 50  return 20
        if vo2max >= 45  return 25
        if vo2max >= 40  return 30
        if vo2max >= 35  return 40
        if vo2max >= 30  return 50
        if vo2max >= 25  return 60
        if vo2max >= 20  return 70
        return 80
```

**Waga w średniej ważonej:** 30%

---

### 2.4 Plank (ćwiczenie izometryczne)

**Cel:** Ocena siły rdzenia (core strength)

**Instrukcja:**
- Przyjmij pozycję plank
- Utrzymaj pozycję jak najdłużej

**Dane wejściowe:**
- `plankTime` - czas w sekundach (0-600)

**Algorytm:**

```
function calculatePlankAge(seconds, gender):
    if gender == 'male':
        if seconds >= 120  return 20
        if seconds >= 90   return 25
        if seconds >= 60   return 30
        if seconds >= 45   return 40
        if seconds >= 30   return 50
        if seconds >= 20   return 60
        if seconds >= 10   return 70
        return 80
    else:  // female
        if seconds >= 90   return 20
        if seconds >= 70   return 25
        if seconds >= 50   return 30
        if seconds >= 35   return 40
        if seconds >= 25   return 50
        if seconds >= 15   return 60
        if seconds >= 8    return 70
        return 80
```

**Waga w średniej ważonej:** 15%

---

### 2.5 WtHR (Waist-to-Height Ratio) - OPCJONALNIE

**Cel:** Ocena ryzyka metabolicznego

**Dane wejściowe:**
- `waist` - obwód talii w cm
- `height` - wzrost w cm

**Obliczenia:**

```
wthr = waist / height

// Interpretacja (uproszczona)
if wthr <= 0.4   return 20   // Bardzo niskie ryzyko
if wthr <= 0.45  return 30   // Niskie ryzyko
if wthr <= 0.5   return 45   // Umiarkowane ryzyko
if wthr <= 0.55  return 60   // Podwyższone ryzyko
return 75                     // Wysokie ryzyko
```

**Waga w średniej ważonej:** 15%

---

## 3. Algorytm Główny

### 3.1 Obliczanie Wieku Funkcjonalnego

```
function calculateFunctionalAge(userData, testResults):
    // Pobierz wiek dla każdego testu
    ages = []
    weights = []
    
    if testResults.flamingo:
        ages.push(calculateFlamingoAge(testResults.flamingo, userData.gender))
        weights.push(0.15)
    
    if testResults.srt:
        ages.push(calculateSRTAge(testResults.srt))
        weights.push(0.25)
    
    if testResults.cooper:
        vo2max = (testResults.cooper - 504.9) / 44.73
        ages.push(calculateCooperAge(vo2max, userData.gender))
        weights.push(0.30)
    
    if testResults.plank:
        ages.push(calculatePlankAge(testResults.plank, userData.gender))
        weights.push(0.15)
    
    // Średnia ważona
    totalWeight = sum(weights)
    functionalAge = sum(ages[i] * weights[i]) / totalWeight
    
    return round(functionalAge)
```

### 3.2 Interpretacja Wyników

| Różnica (wiek metrykalny - funkcjonalny) | Interpretacja |
|-------------------------------------------|---------------|
| > 10 lat | "Jesteś znacznie młodszy/a od swojego wieku!" |
| 5-10 lat | "Bardzo dobry wynik - Twoje ciało jest w świetnej formie." |
| 0-5 lat | "W normie - Twoja sprawność odpowiada wiekowi." |
| -5 lat | "Twoje ciało jest nieco starsze niż wskazuje wiek." |
| < -5 lat | "Warto zadbać o regularną aktywność fizyczną." |

---

## 4. Wymagania Funkcjonalne

### 4.1 Dane Użytkownika (wejście)
- Wiek metrykalny (wymagany)
- Płeć (wymagana)
- Opcjonalnie: wzrost, obwód talii

### 4.2 Dane Wyjściowe
- Wiek funkcjonalny (główny wynik)
- Wiek dla każdego testu osobno
- Porównanie z wiekiem metrykalnym
- Klasyfikacja (młodszy/starszy/norma)

### 4.3 Funkcjonalności
1. **Wprowadzanie danych:** Formularz z polami dla każdego testu
2. **Obliczanie:** Realizacja algorytmów w JS
3. **Wizualizacja:** Wykresy (opcjonalnie Chart.js)
4. **Zapis:** LocalStorage dla historii wyników
5. **Walidacja:** Sprawdzenie poprawności danych wejściowych

---

## 5. Walidacja Danych

| Pole | Typ | Zakres | Komunikat błędu |
|------|-----|--------|-----------------|
| age | integer | 18-100 | "Wprowadź prawidłowy wiek (18-100)" |
| gender | select | male/female | - |
| flamingoTime | float | 0-120 | "Czas musi być między 0 a 120 sekund" |
| srtScore | integer | 0-10 | "Wynik SRT musi być między 0 a 10" |
| cooperDistance | integer | 0-5000 | "Dystans musi być między 0 a 5000 metrów" |
| plankTime | integer | 0-600 | "Czas plank musi być między 0 a 600 sekund" |

---

## 6. Wyjątki i Obsługa Błędów

1. **Brak danych testowych:** Wyświetl komunikat "Wprowadź wyniki przynajmniej jednego testu"
2. **Nieprawidłowe dane:** Podświetl pole na czerwono, pokaż komunikat
3. **LocalStorage niedostępny:** Kontynuuj bez zapisu, wyświetl ostrzeżenie

---

## 7. Technologie (dla projektu studenckiego)

- **HTML5** - struktura strony
- **CSS3** - stylowanie (Flexbox, CSS Variables)
- **JavaScript (ES6+)** - logika aplikacji
- **Opcjonalnie:** Chart.js - wykresy

---

*Specyfikacja wersja 1.0 - Projekt studencki*
