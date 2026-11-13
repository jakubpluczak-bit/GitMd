# Ściąga składni: terminal Linux + Git

**Do czego służy:** gdy na karcie pracy wiesz *co* chcesz zrobić, ale nie pamiętasz *jak to wpisać*.  
**Czym nie jest:** kluczem do zadań. Przykłady mają **inne nazwy i treści** niż na kartach.

### Podział na lekcji: VS Code + terminal

- **VS Code (edytor):** twórz i edytuj treść plików (New File, zapis `Ctrl + S`).
- **Terminal:** katalogi, orientacja, **cały Git**, sprawdzanie efektów, usuwanie ćwiczenia.
- Panel **Source Control** w VS Code dziś pomijamy — ćwiczysz komendy.

### Jak z tego korzystać

1. Najpierw przeczytaj polecenie na karcie i zdecyduj, co chcesz osiągnąć.  
2. Tu znajdź **rodzaj** polecenia.  
3. Dopasuj nazwy katalogów, plików i opisów do **swojego** ćwiczenia.  
4. Po wpisaniu sprawdź efekt (`status`, `ls`, historia).

---

## A. Terminal Linux — orientacja i katalogi

> Tworzenie/edycję **treści plików** możesz robić w VS Code.  
> Poniższe polecenia plikowe (`touch`, `echo`, `cat`) są **opcjonalną alternatywą**, gdy chcesz zostać w terminalu.

### Gdzie jestem?

```bash
pwd
```

**Przykład wyniku (u Ciebie ścieżka może być inna):**

```text
/workspaces/moje-srodowisko
```

---

### Lista zawartości katalogu

```bash
ls
```

Więcej szczegółów:

```bash
ls -la
```

---

### Wejście do katalogu / wyjście wyżej

```bash
cd nazwa-katalogu
cd ..
cd /workspaces
```

**Przykład użycia (inny niż na kartach):**

```bash
cd /workspaces
cd projekt-demo
cd ..
```

---

### Utworzenie katalogu

```bash
mkdir nazwa-katalogu
```

**Przykład:**

```bash
mkdir cwiczenie-wersji
cd cwiczenie-wersji
```

---

### Pliki w VS Code (zalecane na tej lekcji)

1. W eksploratorze po lewej: kliknij ikonę nowego pliku **w katalogu projektu ćwiczeniowego**.  
2. Podaj nazwę, np. `dziennik.txt`.  
3. Wpisz treść w edytorze.  
4. Zapisz (`Ctrl + S`).  
5. W terminalu potwierdź: `ls` (oraz ewentualnie `git status`).

Upewnij się, że plik powstaje **w katalogu ćwiczeniowym**, a nie przypadkiem poza nim.

---

### Pliki w terminalu (opcjonalnie)

Utworzenie pustego pliku:

```bash
touch dziennik.txt
```

Zapis / nadpisanie treści:

```bash
echo "Start projektu demo" > dziennik.txt
```

Dopisanie na końcu:

```bash
echo "Kolejny wpis w dzienniku" >> dziennik.txt
```

Podgląd:

```bash
cat dziennik.txt
```

---

### Usunięcie katalogu projektu (ostrożnie!)

Najpierw wyjdź z katalogu, który kasujesz:

```bash
cd /workspaces
rm -rf nazwa-katalogu
ls
```

**Przykład:**

```bash
cd /workspaces
rm -rf cwiczenie-wersji
ls
```

> Kasuj tylko katalog, który **sam utworzyłeś** do ćwiczenia.

---

## B. Git — lokalne repozytorium

### Inicjalizacja repo od zera (gałąź `main`)

Wejdź najpierw do katalogu projektu, potem:

```bash
git init -b main
```

**Przykład sekwencji:**

```bash
mkdir cwiczenie-wersji
cd cwiczenie-wersji
git init -b main
```

---

### Stan repozytorium (rób to często)

```bash
git status
```

Pokazuje m.in.:

- na której gałęzi jesteś,
- które pliki są nowe / zmienione,
- co jest już przygotowane do commita.

---

### Dodanie wybranego pliku do Staging Area

```bash
git add nazwa-pliku
```

**Przykład:**

```bash
git add dziennik.txt
```

---

### Dodanie zmian z bieżącego katalogu

```bash
git add .
```

Używaj świadomie: trafią tu nowe i zmienione pliki (poza ignorowanymi).

---

### Podgląd różnicy (przed `add` / przed decyzją)

```bash
git diff
```

---

### Zapis punktu historii (commit)

```bash
git commit -m "krotki opis decyzji"
```

**Przykłady opisów (wymyślaj własne na kartach):**

```bash
git commit -m "Dodano dziennik startowy"
git commit -m "Uzupelniono wpis o konfiguracji"
```

---

### Historia

```bash
git log
git log --oneline
git log --oneline --graph
```

**Przykład skróconego widoku:**

```text
b21c9aa Uzupelniono wpis o konfiguracji
9af3102 Dodano dziennik startowy
```

---

### Lista gałęzi

```bash
git branch
```

Gwiazdka `*` oznacza gałąź, na której aktualnie jesteś.

---

### Utworzenie gałęzi

```bash
git branch nazwa-galezi
```

**Przykład (inna nazwa niż na kartach):**

```bash
git branch eksperyment-ui
```

---

### Przełączenie gałęzi

```bash
git switch nazwa-galezi
```

**Przykład:**

```bash
git switch eksperyment-ui
git switch main
```

---

### Scalanie gałęzi

Najpierw przełącz się na gałąź **docelową**, potem:

```bash
git merge nazwa-galezi-zrodlowej
```

**Przykład:**

```bash
git switch main
git merge eksperyment-ui
```

---

## C. Typowe mini-sekwencje (wzorce, nie rozwiązania kart)

### Wzorzec: nowe lokalne repo + pierwszy commit

```bash
mkdir cwiczenie-wersji
cd cwiczenie-wersji
git init -b main
```

Potem w **VS Code** utwórz i zapisz np. `dziennik.txt`, wróć do terminala:

```bash
ls
git status
git add dziennik.txt
git commit -m "Dodano dziennik startowy"
git log --oneline
```

### Wzorzec: kolejna zmiana + commit

W **VS Code** dopisz treść i zapisz plik, potem w terminalu:

```bash
git diff
git add .
git commit -m "Uzupelniono wpis o konfiguracji"
git status
```

### Wzorzec: gałąź → praca → powrót → merge

```bash
git branch eksperyment-ui
git switch eksperyment-ui
```

W **VS Code** zmień plik i dodaj np. `pomysl.txt`, zapisz, potem:

```bash
git add .
git commit -m "Proba nowego ukladu"
git switch main
git merge eksperyment-ui
git log --oneline --graph
```

### Wzorzec: domknięcie (usunięcie ćwiczenia)

```bash
cd /workspaces
rm -rf cwiczenie-wersji
ls
```

---

## D. Ścieżka + (konflikt) — tylko składnia pomocnicza

Konflikt powstaje, gdy dwie gałęzie zmieniają **to samo miejsce** inaczej.  
Po komunikacie o konflikcie:

1. Otwórz plik i znajdź oznaczenia konfliktu.  
2. Ustal ostateczną treść (usuń znaczniki konfliktu).  
3. Dodaj plik ponownie do Staging Area.  
4. Dokończ commit merge.

Przykładowe rodziny poleceń po ręcznej edycji pliku:

```bash
git status
git add nazwa-pliku
git commit -m "Rozstrzygnieto konflikt w pliku"
git log --oneline --graph
```

> Tu celowo **nie ma** gotowego scenariusza „skopiuj i masz konflikt rozwiązany”.  
> Scenariusz jest na karcie (ścieżka +); tu tylko składnia domknięcia.

---

## E. Szybki wybór: chcę… → szukam

| Chcę… | Zacznij od |
|---|---|
| Wiedzieć, gdzie jestem | `pwd` |
| Wejść / wyjść z katalogu | `cd` |
| Utworzyć katalog projektu | `mkdir` |
| Zobaczyć pliki | `ls` |
| Utworzyć / edytować plik | VS Code (albo opcjonalnie `touch` / `echo` / `cat`) |
| Uruchomić historię Gita od zera | `git init -b main` |
| Sprawdzić sytuację | `git status` |
| Wybrać zmiany do zapisu | `git add` |
| Zobaczyć różnicę | `git diff` |
| Zapisać punkt historii | `git commit -m "..."` |
| Zobaczyć historię | `git log --oneline` |
| Pracować na osobnej linii | `git branch` + `git switch` |
| Wciągnąć zmiany do bieżącej gałęzi | `git merge` |
| Usunąć lokalne ćwiczenie | `cd` wyżej + `rm -rf` |

---

## F. Mała zasada bezpieczeństwa

Zanim wpiszesz polecenie niszczące (`rm -rf`) albo zmieniające historię:

1. `pwd` — gdzie jestem?  
2. `ls` / `git status` — co tu jest?  
3. Dopiero wtedy działanie.  
4. Potem znowu sprawdzenie.

Ściąga odblokowuje ręce.  
Karty pracy uczą decyzji.  
Oba materiały działają razem — nie zamiast siebie.
