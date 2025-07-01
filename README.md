Celem tego projektu było przetworzenie, analiza i modelowanie danych filmowych. Należało zaprezentować wybrane sposoby wykrywania błędów w danych oraz na podstawie wyselekcjonowanych cech przeprowadzić uczenie sieci neuronowej.


Projekt służy do przetwarzania danych o filmach oraz przewidywania:

- Czy film **zdobędzie nagrodę** (`Won`)
- Czy dane wejściowe są **poprawne** (`IsCorrect`)

Dodatkowo wykrywa i oznacza błędy w danych w kolumnie `Mistakes`.

## Zawartość danych

Pliki wejściowe:

- `train_data_with_oscars_modifications.txt`
- `validation_data_with_oscars_modifications.txt`
- `test_data_with_oscars_modifications.txt`

**Kolumny:**

- `Title` – tytuł filmu
- `Director` – reżyser
- `Genre` – gatunek filmu
- `Time` – czas trwania (minuty)
- `ReleaseDate` – data premiery (`yyyy-mm-dd`)
- `Rating` – ocena filmu
- `Won` – czy film zdobył nagrodę (`0` lub `1`)


### Parsowanie dat

Daty konwertowane są na liczbę dni od 1 stycznia 1970.

### Wykrywanie błędów

Funkcja `detect_mistakes()` przypisuje błędy:

| Kod | Błąd |
|-----|------|
| `1` | Brak tytułu |
| `2` | Brak lub nieprawidłowy reżyser |
| `3` | Czas trwania poza zakresem (90–230 min) |
| `4` | Nieprawidłowa data premiery |
| `5` | Brak gatunku |
| `6` | Brak oceny |
| `7` | Niepoprawna predykcja `Won` (różni się od etykiety) |

---

## Modele predykcyjne

Użyto dwóch modeli opartych na sieciach neuronowych (Keras):

### Predykcja `Won`
### Predykcja `IsCorrect`


## Ewaluacja

Oba modele uczone są przez 50 epok z użyciem walidacji. Wyświetlane są metryki:

- `loss`
- `accuracy`

---

## Dane wyjściowe

- `test_data_with_updated_mistakes.txt` – dane testowe z predykcjami i błędami
- `test_data_sorted_by_mistakes.txt` – dane posortowane wg liczby błędów

---

## Dodatkowe operacje

- Usunięcie duplikatów
- Konwersja dat z powrotem na `yyyy-mm-dd`
- Obliczanie liczby błędów na wiersz (`Mistakes_digit_count`)
- Sortowanie danych wg liczby błędów


### Wymagania dodatkowe

pip install pandas numpy scikit-learn keras




