# Świąteczna Koza AR — paczka wdrożeniowa

Wgraj **zawartość tej paczki** do katalogu publicznego serwera. Wszystkie pliki muszą leżeć obok siebie, w tym samym katalogu co `index.html`.

## Wymagania

- HTTPS albo `localhost` — inaczej przeglądarka zablokuje kamerę.
- Dostęp do kamery po stronie użytkownika.
- Serwer statyczny; nie jest potrzebny backend.

## Pliki

| Plik | Rola |
|---|---|
| `index.html` | scena AR |
| `koza.patt` | wzór markera |
| `koza.webm` | animacja z przezroczystym tłem (VP9 alpha) |
| `koza.mp4` | fallback dla przeglądarek bez WebM alpha |
| `marker-print.png` | marker do druku / wyświetlenia |
| `marker-print-A4.pdf` | marker na A4, gotowy do druku |

## Marker

Wydrukuj `marker-print-A4.pdf` w skali **100%** albo `marker-print.png` w dowolnym rozmiarze. Zachowaj całą grubą czarną ramkę i białe pole wokół niej. Nie przycinaj krawędzi.

Marker najlepiej działa na płaskiej, matowej powierzchni, przy równomiernym świetle. Odległość startowa: około 30–50 cm.

`koza.patt` jest dopasowany do `marker-print.png`. Nie podmieniaj markera bez wygenerowania nowego pliku `.patt`.

## Jak to działa

- A-Frame 1.6.0 renderuje scenę.
- AR.js 3.4.8 śledzi marker `koza.patt`.
- Po wykryciu markera odtwarzana jest animacja.
- `koza.webm` ma kanał alfa, więc tło jest przezroczyste.
- Jeśli przeglądarka nie obsługuje VP9 alpha, użyje `koza.mp4` — wtedy tło będzie białe.
- Jeśli autoplay zostanie zablokowany, pojawi się prośba o dotknięcie ekranu.

## Rozwiązywanie problemów

### Kamera nie startuje

- Otwórz stronę przez HTTPS albo `http://localhost`.
- Zezwól na kamerę w ustawieniach przeglądarki.
- Zamknij inne aplikacje używające kamery.
- Na iOS użyj Safari; na Androidzie Chrome.

### Marker nie jest wykrywany

- Wydrukuj `marker-print-A4.pdf` w 100%.
- Upewnij się, że cała czarna ramka jest widoczna.
- Popraw oświetlenie; unikaj odblasków i cienia.
- Zbliż lub oddal kamerę; marker powinien zajmować znaczną część kadru.
- Wyczyść szybkę kamery.

### Koza ma białe tło

- Przeglądarka nie obsługuje przezroczystego WebM. Użyj Chrome, Edge albo Firefoksa.
- Safari może wybrać `koza.mp4`; to zamierzone zachowanie fallbacku.

### Animacja się nie odtwarza

- Dotknij ekranu.
- Sprawdź, czy plik `koza.webm` jest dostępny pod właściwym adresem.
- Sprawdź konsolę przeglądarki.

## Techniczne

- A-Frame: `1.6.0` (CDN `aframe.io`)
- AR.js: `3.4.8` (CDN jsDelivr, wersja przypięta)
- Marker: custom pattern
- Wideo: VP9 `yuva420p`, 1080×1080, 24 fps, 10 klatek, pętla
- Fallback: H.264 MP4, 1080×1080

Pliki źródłowe i skrypty regeneracji znajdują się w repozytorium projektu, nie w tej paczce.
