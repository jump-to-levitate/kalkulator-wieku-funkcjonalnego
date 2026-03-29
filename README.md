# 🧬 BioAge: Functional Performance SaaS

**BioAge** to zaawansowane narzędzie analityczne typu SPA (Single Page Application), które przekłada surowe dane biomedyczne i wydolnościowe na zrozumiały wskaźnik: **Wiek Funkcjonalny**. 

---

## 🗺️ Nawigacja po Projekcie
Szybki dostęp do dokumentacji strategicznej i technicznej:

* **[🏠 Strona Główna](#-kluczowe-filary-projektu)**
* **[💡 Strategia Produktu](./docs/01-opis-pomyslu.md)** – Wizja, problem i katalog testów.
* **[⚙️ Specyfikacja Funkcjonalna](./docs/02-specyfikacja-funkcjonalna.md)** – Algorytmy i opis testów (Flamingo, SRT, Cooper).
* **[📊 Model Danych](./docs/03-model-danych.md)** – Struktura obiektów JS i LocalStorage.
* **[👥 Analiza Persony (ICP)](./docs/icp-persona.md)** – Kto jest naszym użytkownikiem?
* **[🎯 Analiza JTBD](./docs/jtbd-analysis.md)** – Jakie problemy rozwiązujemy?
* **[🚩 Raport Audytowy](./docs/kill-the-idea-report.md)** – Krytyczna analiza biznesowa (Kill the Idea).

---

## 🚀 Kluczowe Filary Projektu

### 1. Diagnostyka Wielowymiarowa
Aplikacja agreguje dane z 5 kluczowych domen:
* **Cardiovascular (VO2max):** Wydolność serca i płuc (Test Coopera).
* **Neuromuscular:** Równowaga i koordynacja (Próba Flamingo).
* **Musculoskeletal:** Siła relatywna i mobilność (SRT, Plank).
* **Metabolic & Anthropometric:** Wskaźnik WtHR (talia/wzrost).
* **Metabolic:** Estymacja na podstawie tętna spoczynkowego.

### 2. Silnik Analityczny (JS Engine)
* **Normalizacja danych:** Przeliczanie wyników na percentyle wiekowe.
* **Algorytm Agregujący:** Obliczanie średniej ważonej (Wydolność: 30%, Mobilność: 25%, Pozostałe: 15%).

### 3. Wizualizacja "Data-to-Action"
Zastosowanie bibliotek JS (Chart.js) do generowania:
* **Linear Aging Curve:** Twoja pozycja na krzywej regresji sprawności.
* **Biological Gap:** Różnica między wiekiem metrykalnym a funkcjonalnym.

---

## 🛠 Stos Technologiczny (Tech Stack)
* **Core:** HTML5, CSS3, Modern JavaScript (ES11+).
* **Charts:** Chart.js dla lekkości i responsywności.
* **Storage:** LocalStorage (Privacy-by-Design).

---
*BioAge: Measure what matters. Stay functional.*
