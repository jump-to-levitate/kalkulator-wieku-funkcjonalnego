# 03. Model Danych: BioAge

## Projekt Studencki - Kalkulator Wieku Funkcjonalnego

---

## 1. Struktury Danych w JavaScript

### 1.1 Obiekt Użytkownika

```javascript
const user = {
    id: string,           // UUID lub timestamp
    age: number,          // wiek metrykalny (18-100)
    gender: string,        // 'male' | 'female'
    height: number,       // wzrost w cm (opcjonalnie)
    waist: number,        // obwód talii w cm (opcjonalnie)
    createdAt: timestamp, // data utworzenia
    updatedAt: timestamp  // data ostatniej edycji
}
```

### 1.2 Obiekt Wyników Testu

```javascript
const testResults = {
    flamingo: {
        time: number,         // czas w sekundach
        age: number,          // obliczony wiek
        timestamp: timestamp
    },
    srt: {
        score: number,        // punkty (0-10)
        age: number,         // obliczony wiek
        timestamp: timestamp
    },
    cooper: {
        distance: number,     // dystans w metrach
        vo2max: number,      // obliczone VO2max
        age: number,         // obliczony wiek
        timestamp: timestamp
    },
    plank: {
        time: number,         // czas w sekundach
        age: number,          // obliczony wiek
        timestamp: timestamp
    }
}
```

### 1.3 Pełny Obiekt Wyniku (do zapisu)

```javascript
const assessment = {
    id: string,                    // UUID
    userId: string,                 // ID użytkownika
    userData: {
        age: number,
        gender: string,
        height: number | null,
        waist: number | null
    },
    testResults: {
        flamingo: { time: number, age: number } | null,
        srt: { score: number, age: number } | null,
        cooper: { distance: number, vo2max: number, age: number } | null,
        plank: { time: number, age: number } | null
    },
    calculatedAge: number,          // wynik końcowy
    comparison: {
        difference: number,         // wiek metrykalny - funkcjonalny
        classification: string      // 'younger' | 'same' | 'older'
    },
    timestamp: timestamp
}
```

---

## 2. Struktura LocalStorage

### 2.1 Klucze

| Klucz | Typ | Opis |
|-------|-----|------|
| `bioage_user` | object | Aktualny użytkownik |
| `bioage_history` | array | Historia wyników |
| `bioage_settings` | object | Ustawienia aplikacji |

### 2.2 Format Danych w LocalStorage

```javascript
// bioage_user
localStorage.setItem('bioage_user', JSON.stringify({
    age: 30,
    gender: 'male',
    height: 180,
    waist: 85,
    updatedAt: '2026-03-15T18:00:00Z'
}));

// bioage_history
localStorage.setItem('bioage_history', JSON.stringify([
    {
        id: 'uuid-1',
        timestamp: '2026-03-15T18:00:00Z',
        userData: { age: 30, gender: 'male' },
        testResults: {
            flamingo: { time: 25, age: 30 },
            srt: { score: 8, age: 30 },
            cooper: { distance: 2400, vo2max: 42.3, age: 35 },
            plank: { time: 60, age: 30 }
        },
        calculatedAge: 31,
        comparison: { difference: -1, classification: 'same' }
    },
    {
        id: 'uuid-2',
        timestamp: '2026-03-01T18:00:00Z',
        // ... kolejny wynik
    }
]));

// bioage_settings
localStorage.setItem('bioage_settings', JSON.stringify({
    theme: 'light',
    unitSystem: 'metric',
    chartsEnabled: true,
    lastOpened: '2026-03-15T18:00:00Z'
}));
```

---

## 3. Schemat JSON (dla dokumentacji)

### 3.1 Schema.org Medical entity (rozszerzenie)

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Unikalny identyfikator oceny"
    },
    "subject": {
      "type": "object",
      "properties": {
        "age": { "type": "integer", "minimum": 18, "maximum": 100 },
        "gender": { "type": "string", "enum": ["male", "female"] }
      },
      "required": ["age", "gender"]
    },
    "tests": {
      "type": "object",
      "properties": {
        "flamingo": {
          "type": "object",
          "properties": {
            "value": { "type": "number" },
            "unit": { "type": "string", "const": "seconds" },
            "resultAge": { "type": "integer" }
          }
        },
        "srt": {
          "type": "object",
          "properties": {
            "value": { "type": "integer" },
            "unit": { "type": "string", "const": "points" },
            "resultAge": { "type": "integer" }
          }
        },
        "cooper": {
          "type": "object",
          "properties": {
            "value": { "type": "integer" },
            "unit": { "type": "string", "const": "meters" },
            "vo2max": { "type": "number" },
            "resultAge": { "type": "integer" }
          }
        },
        "plank": {
          "type": "object",
          "properties": {
            "value": { "type": "integer" },
            "unit": { "type": "string", "const": "seconds" },
            "resultAge": { "type": "integer" }
          }
        }
      }
    },
    "result": {
      "type": "object",
      "properties": {
        "functionalAge": { "type": "integer" },
        "chronologicalAge": { "type": "integer" },
        "difference": { "type": "integer" },
        "classification": {
          "type": "string",
          "enum": ["much_younger", "younger", "same", "older", "much_older"]
        }
      },
      "required": ["functionalAge"]
    }
  },
  "required": ["subject", "tests", "result"]
}
```

---

## 4. Przykładowe Dane (dla testów)

### 4.1 Przykład 1: Młody sportowiec

```javascript
const exampleYoung = {
    userData: { age: 25, gender: 'male' },
    testResults: {
        flamingo: { time: 35, age: 20 },
        srt: { score: 10, age: 20 },
        cooper: { distance: 3000, vo2max: 55.8, age: 20 },
        plank: { time: 120, age: 20 }
    },
    calculatedAge: 20,
    comparison: { difference: 5, classification: 'younger' }
};
```

### 4.2 Przykład 2: Osoba starsza

```javascript
const exampleOlder = {
    userData: { age: 55, gender: 'female' },
    testResults: {
        flamingo: { time: 8, age: 65 },
        srt: { score: 5, age: 60 },
        cooper: { distance: 1500, vo2max: 22.2, age: 70 },
        plank: { time: 15, age: 60 }
    },
    calculatedAge: 64,
    comparison: { difference: -9, classification: 'older' }
};
```

---

## 5. Funkcje Pomocnicze (API)

### 5.1 Zapis i Odczyt

```javascript
// Zapisz wynik
function saveAssessment(assessment) {
    const history = JSON.parse(localStorage.getItem('bioage_history') || '[]');
    history.unshift(assessment);  // Dodaj na początek
    localStorage.setItem('bioage_history', JSON.stringify(history));
}

// Pobierz historię
function getHistory() {
    return JSON.parse(localStorage.getItem('bioage_history') || '[]');
}

// Wyczyść historię
function clearHistory() {
    localStorage.removeItem('bioage_history');
}
```

### 5.2 Walidacja

```javascript
function validateAge(age) {
    return Number.isInteger(age) && age >= 18 && age <= 100;
}

function validateTestTime(time, max = 120) {
    return typeof time === 'number' && time >= 0 && time <= max;
}

function validateSRTScore(score) {
    return Number.isInteger(score) && score >= 0 && score <= 10;
}
```

---

## 6. Diagram Klas (UML)

```
┌─────────────────┐       ┌──────────────────┐
│    UserData     │       │   TestResult     │
├─────────────────┤       ├──────────────────┤
│ - age: number   │       │ - time: number   │
│ - gender: string│       │ - score: number  │
│ - height: number│       │ - distance: number│
│ - waist: number │       │ - age: number    │
└─────────────────┘       └──────────────────┘
         │                        │
         └────────┬───────────────┘
                  │
         ┌────────▼────────┐
         │   Assessment    │
         ├─────────────────┤
         │ - id: string    │
         │ - userData      │
         │ - testResults   │
         │ - calculatedAge │
         │ - timestamp     │
         └─────────────────┘
```

---

*Model danych wersja 1.0 - Projekt studencki*
