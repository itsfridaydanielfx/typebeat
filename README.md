# jaki to type beat

Mała statyczna apka — wpisujesz artystę / numer / link / notatkę, a AI odpowiada jakich type beatów najpewniej używa.

## Jak to działa

- Czysty HTML/CSS/JS, bez backendu, hostuje się na GitHub Pages.
- AI to Google **Gemini 2.0 Flash** przez darmowy klucz z [aistudio.google.com/apikey](https://aistudio.google.com/apikey) (~1500 zapytań/dzień za darmo, bez karty).
- Klucz wpisujesz raz, zapisuje się tylko w `localStorage` twojej przeglądarki — nigdzie nie jest wysyłany poza Google.
- Odpowiedzi są deterministyczne (`temperature: 0`) i dodatkowo cache'owane lokalnie po haszu inputu — to samo zapytanie zawsze zwraca to samo.
- Model jest ograniczony promptem systemowym wyłącznie do tematu type beatów / muzyki — inne pytania odbija.

## Deploy na GitHub Pages

1. Stwórz repo na GitHubie, wrzuć wszystkie pliki (`index.html`, `style.css`, `app.js`, `README.md`).
2. W repo: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)` → Save**.
3. Po chwili strona będzie na `https://<user>.github.io/<repo>/`.

## Lokalnie

Wystarczy otworzyć `index.html` w przeglądarce. Albo:

```
python -m http.server 8000
```

## Kontekst który możesz wkleić

- sam artysta — `Young Multi`
- artysta + numer — `Young Multi - Lambo`
- link YouTube — model potraktuje go jako wskazówkę kontekstową (nie analizuje audio)
- własna notatka — `gęste 808, autotune, ciemny ambient`
- pytanie naturalne — `jakich bitów używa Białas?`
