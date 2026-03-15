# 01. Strategia Produktu: BioAge

## 1. Definicja Problemu
Współczesne społeczeństwo starzeje się w sposób niejednolity. Osoba 40-letnia może mieć wydolność 25-latka lub 60-latka. Istniejące aplikacje fitness skupiają się na *wyglądzie* (kalorie, kroki) lub *wynikach sportowych*, ignorując kluczowy aspekt: **zdrowie funkcjonalne i długowieczność (longevity)**.

**Główne bolączki użytkowników:**
* Brak wiedzy, jak ich sprawność odnosi się do norm medycznych.
* Trudność w interpretacji wyników takich jak VO2max (co to oznacza dla mojego życia?).
* Lęk przed utratą sprawności w przyszłości.

## 2. Rozwiązanie (Value Proposition)
BioAge to "lustro biologiczne". Dostarczamy narzędzie, które poprzez serię prostych testów domowych (i terenowych) tworzy profil wieku biologicznego. 

**Unikalna wartość:**
* **Niskie bariery wejścia:** Większość testów nie wymaga sprzętu (np. test wstawania z podłogi).
* **Natychmiastowa gratyfikacja/Feedback:** Użytkownik od razu widzi: "Twoje serce ma 32 lata".

## 3. Szczegółowy Katalog Testów i Metryk

Aplikacja implementuje następujące protokoły badawcze:

### A. Domena: Stabilność i Układ Nerwowy
1.  **Próba Flamingo (Unipedal Stance Test):** Stanie na jednej nodze z zamkniętymi oczami.
    * *Wiek 20-30:* > 25-30 sek.
    * *Wiek 50+:* < 10 sek. oznacza wysokie ryzyko upadków.
2.  **Test Reakcji (Drop Ruler Test):** Chwytanie spadającej linijki – ocena wieku układu nerwowego.

### B. Domena: Mobilność i Siła Funkcjonalna
3.  **Sitting-Rising Test (SRT):** Siad skrzyżny i powstanie bez użycia rąk. Każde podparcie to -1 punkt. 
    * *Wynik < 8 pkt:* Koreluje statystycznie z krótszą przewidywaną długością życia.
4.  **Wall Sit (Krzesełko przy ścianie):** Wytrzymałość siłowa dołu ciała.

### C. Domena: Wydolność Krążeniowo-Oddechowa
5.  **Test Coopera (12 min):** Estymacja VO2max za pomocą wzoru: $VO2max = (Dystans - 504.9) / 44.73$.
6.  **Harvard Step Test:** Pomiar wydolności na podstawie szybkości powrotu tętna do normy po 5 min wchodzenia na stopień.
   
### C. Metryki Antropometryczne (Nowość)
1. **Waist-to-Height Ratio (WtHR):** Najdokładniejszy domowy wskaźnik otłuszczenia narządów wewnętrznych.
2. **Body Mass Index (BMI):** Jako parametr pomocniczy (tradycyjny).


---

## 4. Koncepcja Wizualizacji (Dashboard)

Wykresy w BioAge nie mają tylko informować – mają motywować do zmiany.

### Wykres 1: Biologiczny "Lollipop Chart"
Oś pionowa to wiek. Dwie kropki połączone linią dla każdego testu: jedna to wiek metrykalny (stała), druga to wiek wynikowy. 
* *Interpretacja:* Jeśli kropka wyniku jest poniżej linii wieku metrykalnego – odmładzasz się.

### Wykres 2: Cross-Sectional Comparison (Linia trendu)
Wykres liniowy pokazujący spadek sprawności z wiekiem w populacji (np. spadek VO2max o 1% rocznie). 
* **Dynamiczna warstwa JS:** Użytkownik widzi swoją pozycję jako punkt na tej krzywej i może przesunąć suwak, by zobaczyć: "Gdzie będę za 10 lat, jeśli nie poprawię wyników?".

### Wykres 3: Radar "Functional Balance"
Pięciokąt pokazujący: Siłę, Wydolność, Równowagę, Mobilność, Szybkość. 
* *Cel:* Identyfikacja "najsłabszego ogniwa" (np. świetne serce, ale fatalna mobilność).

---

## 5. Przewagi Konkurencyjne
* **Scientific Approach:** Każdy test posiada bibliografię i oparcie w badaniach (np. ACSM, badania dr. Araujo).
* **Privacy First:** Brak konieczności zakładania konta dla podstawowych obliczeń (wszystko liczone w JS po stronie klienta).