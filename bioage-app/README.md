# 🧬 BioAge: Functional Performance SaaS

**BioAge** to zaawansowane narzędzie analityczne typu SPA (Single Page Application), które przekłada surowe dane biomedyczne i wydolnościowe na zrozumiały wskaźnik: **Wiek Funkcjonalny**. 

W świecie, gdzie "70 to nowe 50", nasza aplikacja pozwala użytkownikom obiektywnie zmierzyć tempo starzenia się ich organizmu i zidentyfikować "wąskie gardła" ich sprawności.

---

## 🚀 Kluczowe Filary Projektu

### 1. Diagnostyka Wielowymiarowa
Aplikacja nie opiera się na jednym teście. Agreguje dane z 4 kluczowych domen:
* **Cardiovascular (VO2max):** Wydolność serca i płuc.
* **Neuromuscular:** Równowaga, czas reakcji, koordynacja.
* **Musculoskeletal:** Siła relatywna i mobilność stawów.
* **Metabolic & Anthropometric:** Wskaźniki składu ciała (w tym kluczowy **WtHR**).
* **Metabolic:** Estymacja na podstawie tętna spoczynkowego i regeneracji.

### 2. Silnik Analityczny (JS Engine)
* **Normalizacja danych:** Przeliczanie wyników (metry, sekundy, powtórzenia) na percentyle w grupach wiekowych.
* **Algorytm Agregujący:** Obliczanie średniej ważonej z uwzględnieniem priorytetów (np. wydolność krążeniowa ma wyższą wagę w ocenie długowieczności niż elastyczność).

### 3. Wizualizacja "Data-to-Action"
Zastosowanie bibliotek JS (Chart.js/ApexCharts) do generowania:
* **Linear Aging Curve:** Twoja pozycja na krzywej regresji sprawności.
* **Biological Gap:** Wizualizacja różnicy między wiekiem metrykalnym a funkcjonalnym.

---

## 🛠 Stos Technologiczny (Tech Stack)
* **Core:** HTML5, CSS3 (Custom Variables, Flexbox/Grid), Modern JavaScript (ES11+).
* **Content:** Markdown (wykorzystywany jako CMS do instrukcji testów i treści edukacyjnych).
* **Charts:** Chart.js dla lekkości i responsywności.
* **Storage:** LocalStorage (dla zachowania prywatności danych użytkownika - model Privacy-by-Design).

## 📂 Struktura Dokumentacji (Metodyka ABS)
Zgodnie ze standardem *Architekta Biznesu SaaS*, projekt podzielono na:
1.  `01-opis-pomyslu.md` - Strategia, Problem, Rozwiązanie.
2.  `02-specyfikacja-funkcjonalna.md` - Opis logiki testów i algorytmów. (Wkrótce)
3.  `03-model-danych.md` - Struktura obiektów JS i mapowanie wyników. (Wkrótce)

---
*BioAge: Measure what matters. Stay functional.*