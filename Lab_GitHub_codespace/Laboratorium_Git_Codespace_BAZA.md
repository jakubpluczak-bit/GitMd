# Laboratorium: Git w terminalu (GitHub Codespaces)

## Plik bazowy pod materiały dla uczniów

> **Rola tego pliku:** konspekt / źródło do przygotowania karty ucznia, prezentacji lub checklisty.  
> **Środowisko:** GitHub Codespaces = wypożyczony Linux + terminal (obejście braku Gita na stanowiskach szkolnych).  
> **Przedmiot lekcji:** lokalny Git w terminalu, nie GitHub jako serwis współpracy.  
> **Trwałość repo:** nie jest wymagana — repo może powstać i zniknąć w czasie jednej lekcji.

---

# 0. Ramka dla ucznia (do skopiowania na początek materiałów)

Dzisiaj ćwiczysz **Git w prawdziwym terminalu**.

- **GitHub** i **Codespaces** służą tylko do uruchomienia środowiska.
- Pracujesz w **osobnym katalogu ćwiczeniowym**, nie w repozytorium utworzonym na GitHubie.
- Po ćwiczeniu **usuwasz** lokalne repo (i najlepiej Codespace) — nic nie musi „przetrwać”.

---

# Cel ćwiczenia

Po wykonaniu zadań uczeń potrafi:

- utworzyć lokalne repozytorium (`git init`),
- sprawdzać stan repozytorium (`git status`),
- dodawać pliki do Staging Area (`git add`),
- tworzyć commity (`git commit`),
- przeglądać historię (`git log`),
- tworzyć i przełączać gałęzie (`git branch`, `git switch`),
- scalać gałęzie (`git merge`),
- **zamknąć cykl życia repo** przez jego usunięcie.

---

# Efekty / kryteria sukcesu (checklista końcowa)

Uczeń zalicza ćwiczenie, gdy w terminalu potrafi wykazać:

1. Istnieje katalog ćwiczeniowy z lokalnym repo (katalog `.git`).
2. Historia zawiera **co najmniej 3 commity** (np. `git log --oneline`).
3. Istnieje gałąź dodatkowa (np. `funkcja`) obok `main`.
4. Po `merge` na `main` widać zmiany z gałęzi (plik/tekst z gałęzi jest obecny).
5. Po zakończeniu katalog ćwiczeniowy został **usunięty** (`ls` go nie pokazuje).

---

# 1. Czym jest Git? (krótko)

Git to system kontroli wersji. Zapisuje historię zmian w plikach projektu.

Dzięki Git możesz:

- wrócić do wcześniejszej wersji,
- zobaczyć, kto i kiedy wprowadził zmianę,
- rozwijać warianty projektu na gałęziach,
- scalać zmiany.

**Git** ≠ **GitHub** ≠ **Codespaces**

| Pojęcie | Znaczenie na tej lekcji |
|---|---|
| Git | Program w terminalu do historii projektu |
| GitHub | Serwis potrzebny do założenia konta i odpalenia Codespace |
| Codespaces | Komputer w chmurze z terminalem Linux |

---

# 2. Podstawowe pojęcia

## Repozytorium

Katalog projektu z historią zmian Git. Po `git init` powstaje ukryty katalog `.git`.

## Working Directory

Katalog roboczy — aktualne pliki, które edytujesz. Zmiany **nie** trafiają automatycznie do historii.

## Staging Area

Obszar przygotowania zmian (indeks). „Koszyk” zmian wybranych do następnego commita.

```text
Working Directory
        │  git add
        ▼
   Staging Area
        │  git commit
        ▼
      Historia (commit)
```

## Commit

Zapisany punkt kontrolny projektu (identyfikator, autor, data, opis).

## Branch (gałąź)

Niezależna linia rozwoju. Domyślnie pracujesz na `main`.

---

# 3. Start środowiska (bootstrap — nie jest „nauką GitHub”)

Te kroki służą wyłącznie do otwarcia terminala w chmurze.

## 3.1. Konto GitHub

1. Wejdź na https://github.com
2. `Sign Up` → e-mail, hasło, nazwa użytkownika
3. Potwierdź e-mail i zaloguj się

## 3.2. Repozytorium nośnikowe (tylko do Codespace)

1. `New Repository`
2. Nazwa np. `laboratorium-git`
3. `Public`
4. Zaznacz `Add a README file`
5. `Create repository`

> To repo jest **nośnikiem środowiska**. Ćwiczenie Gita robisz w **innym** katalogu.

## 3.3. Uruchomienie Codespace

1. W repozytorium: `Code` → `Codespaces`
2. `Create codespace on main`
3. Poczekaj na VS Code w przeglądarce

## 3.4. Terminal

`Terminal → New Terminal` lub `Ctrl + ``

Powinien pojawić się terminal Linux.

---

# 4. Cykl życia lokalnego repozytorium

## Etap A — utworzenie

Sprawdź, gdzie jesteś:

```bash
pwd
```

Przejdź do katalogu nadrzędnego workspace:

```bash
cd /workspaces
```

> Po starcie Codespace terminal często jest już w `/workspaces/laboratorium-git`.  
> **Wyjdź z tego katalogu** — nie ćwiczysz w repo nośnikowym.

Utwórz katalog ćwiczeniowy i wejdź do niego:

```bash
mkdir git-laboratorium
cd git-laboratorium
```

Utwórz lokalne repozytorium na gałęzi `main`:

```bash
git init -b main
```

Oczekiwany komunikat w stylu:

```text
Initialized empty Git repository in ...
```

Sprawdź stan:

```bash
git status
```

Przykład:

```text
On branch main
No commits yet
nothing to commit
```

---

## Etap B — pierwsze pliki i commity

### B1. Plik

```bash
touch notatka.txt
echo "Moj pierwszy plik w repozytorium Git" > notatka.txt
cat notatka.txt
```

### B2. Status (untracked)

```bash
git status
```

Oczekiwane: `Untracked files` → `notatka.txt`

### B3. Staging

```bash
git add notatka.txt
git status
```

Oczekiwane: `Changes to be committed`

### B4. Commit

```bash
git commit -m "Dodano plik notatka.txt"
```

### B5. Historia

```bash
git log --oneline
```

---

## Etap C — kolejna zmiana w tym samym pliku

```bash
echo "Druga linia tekstu" >> notatka.txt
cat notatka.txt
git status
```

Opcjonalnie (warto pokazać uczniom różnicę przed `add`):

```bash
git diff
```

Dodanie wszystkich zmian z bieżącego katalogu (w tym nowych plików, poza ignorowanymi):

```bash
git add .
git status
git commit -m "Dodano druga linie tekstu"
git log --oneline
```

---

## Etap D — gałąź, praca równoległa, powrót

### D1. Utworzenie gałęzi

```bash
git branch funkcja
git branch
```

Gwiazdka `*` oznacza bieżącą gałąź (`main`).

### D2. Przełączenie

```bash
git switch funkcja
git branch
```

### D3. Zmiany na gałęzi `funkcja`

```bash
echo "Zmiana wykonana w galezi funkcja" >> notatka.txt
touch opis.txt
echo "Plik utworzony na galezi funkcja" > opis.txt
git status
```

Powinny być widoczne:

- zmodyfikowany `notatka.txt`,
- nowy `opis.txt`.

```bash
git add .
git commit -m "Rozwoj funkcji"
git log --oneline
```

### D4. Powrót na `main` i obserwacja

```bash
git switch main
cat notatka.txt
ls
```

Zmiany z gałęzi `funkcja` **nie są jeszcze** na `main`.  
Gałęzie przechowują osobne linie historii.

---

## Etap E — scalanie

```bash
git merge funkcja
```

W tym scenariuszu (brak nowych commitów na `main` po odgałęzieniu) zwykle zobaczysz:

```text
Fast-forward
```

Sprawdzenie:

```bash
cat notatka.txt
ls
git log --oneline --graph
```

Oczekiwane:

- w `notatka.txt` jest linia z gałęzi `funkcja`,
- istnieje `opis.txt`,
- historia pokazuje commit `Rozwoj funkcji`.

---

## Etap F — usunięcie repozytorium (zamknięcie cyklu)

To jest świadomy koniec życia lokalnego repo ćwiczeniowego.

1. Wyjdź z katalogu repo:

```bash
cd /workspaces
```

2. Usuń cały katalog projektu (wraz z `.git`):

```bash
rm -rf git-laboratorium
```

3. Potwierdź:

```bash
ls
```

Katalog `git-laboratorium` nie powinien być widoczny.

4. (Zalecane po lekcji) Zamknij / usuń Codespace w GitHubie, żeby nie zużywać limitu.

> Usunięcie katalogu = usunięcie lokalnego repo.  
> Repozytorium nośnikowe na GitHubie możesz zostawić na kolejne zajęcia albo też usunąć (`Settings` → `Delete this repository`).

---

# 5. Mapa poleceń (ściąga)

```bash
pwd
cd
mkdir
ls
touch
echo
cat
rm -rf

git init -b main
git status
git add
git diff
git commit -m "opis"
git log --oneline
git log --oneline --graph
git branch
git switch
git merge
```

Przepływ:

```text
Utworzenie katalogu + git init
        │
        ▼
Edycja plików (Working Directory)
        │  git add
        ▼
Staging Area
        │  git commit
        ▼
Historia
        │
        ▼
Gałęzie → merge
        │
        ▼
Usunięcie katalogu repo (koniec cyklu)
```

---

# 6. FAQ / typowe problemy (dla nauczyciela i karty pomocy)

| Objaw | Co zwykle jest nie tak | Co zrobić |
|---|---|---|
| „Na GitHubie nic nie widać” | Ćwiczenie jest lokalne, bez `push` | To zamierzone — sprawdzamy lokalnie `git log` |
| Panel Source Control w VS Code pokazuje dziwne zmiany | Otwarte jest repo nośnikowe, nie ćwiczeniowe | `cd /workspaces/git-laboratorium` i pracuj w terminalu |
| Po `git init` jest `master` zamiast `main` | Użyto samego `git init` | Użyj `git init -b main` |
| `git commit` pyta o tożsamość | Rzadkie w Codespaces | W Codespaces zwykle ustawione z profilu GitHub |
| Po `switch main` zniknęły zmiany | To poprawne przed merge | Najpierw commit na gałęzi, potem `merge` |
| `rm -rf` skasowało za dużo | Zła ścieżka | Zawsze `cd /workspaces`, potem usuń tylko `git-laboratorium` |

---

# 7. Notatki do przygotowania materiałów uczniowskich

Z tego pliku bazowego można szybko zrobić:

1. **Kartę ucznia** — sekcje 0, 3 (skrót), 4 (same komendy + „oczekiwane”), checklista z § „Efekty”.
2. **Prezentację 10–12 slajdów** — Git vs GitHub vs Codespaces → 3 obszary → demo commit → gałąź → merge → usunięcie.
3. **Kartę nauczyciela** — FAQ (§6), limity Codespaces, przypomnienie o usunięciu środowiska po lekcji.
4. **Mini-sprawdzian praktyczny** — „pokaż 3 commity + merge + usuń repo” (bez oceniania remote).

Szacowany czas: **45–60 min** (bootstrap konta/Codespace może zająć sporo przy pierwszym razie; warto założyć konta wcześniej).

---

# 8. Relacja do szkicu

Plik powstał na bazie szkicu `Laboratorium Git w GitHub Codespace.md`, z doprecyzowaniem:

- Codespace = środowisko, nie cel lekcji,
- osobne repo ćwiczeniowe vs repo nośnikowe,
- `git init -b main`,
- domknięcie cyklu przez usunięcie,
- checklista sukcesu i FAQ.
