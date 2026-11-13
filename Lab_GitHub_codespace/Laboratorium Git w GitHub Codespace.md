# Laboratorium Git w GitHub Codespaces
## Tworzenie repozytorium za pomocą `git init`, commitowanie zmian, praca na gałęziach i scalanie

---

# Cel ćwiczenia

Celem ćwiczenia jest poznanie podstaw działania systemu kontroli wersji Git. Po wykonaniu wszystkich zadań uczeń będzie potrafił:

- utworzyć lokalne repozytorium Git,
- sprawdzać stan repozytorium,
- dodawać pliki do obszaru przygotowania zmian (Staging Area),
- tworzyć commity,
- przeglądać historię zmian,
- tworzyć gałęzie (branch),
- przełączać się między gałęziami,
- scalać gałęzie,
- rozumieć podstawowe elementy działania Git.

---

# 1. Czym jest Git?

Git jest systemem kontroli wersji. Jego zadaniem jest zapisywanie historii zmian wykonywanych w plikach projektu.

Dzięki Git możemy:

- wrócić do starszej wersji pliku,
- sprawdzić, kto wprowadził określone zmiany,
- pracować nad różnymi wersjami projektu jednocześnie,
- bezpiecznie scalać zmiany wykonane przez różnych programistów.

---

# 2. Podstawowe pojęcia

## Repozytorium

Repozytorium (repository) to katalog projektu zawierający historię wszystkich zmian zapisanych przez Git.

Po utworzeniu repozytorium Git dodaje ukryty katalog:

```text
.git
```

To właśnie w nim przechowywane są informacje o historii projektu.

---

## Working Directory

Working Directory (katalog roboczy) zawiera aktualnie edytowane pliki projektu.

Przykład:

```text
projekt/
├── index.html
├── style.css
└── script.js
```

Zmiany wykonywane w plikach nie są automatycznie zapisywane w historii Git.

---

## Staging Area

Staging Area (obszar przygotowania zmian, indeks Git) jest miejscem przejściowym pomiędzy plikami projektu a historią commitów.

Można powiedzieć, że jest to koszyk, do którego wkładamy zmiany przeznaczone do zapisania.

Schemat działania:

```text
Working Directory
        │
        ▼
   Staging Area
        │
        ▼
      Commit
```

---

## Commit

Commit jest zapisanym punktem kontrolnym projektu.

Każdy commit posiada:

- identyfikator,
- autora,
- datę,
- opis zmian.

Przykład:

```text
Dodano stronę główną
```

---

## Branch

Branch (gałąź) jest niezależną linią rozwoju projektu.

Najczęściej spotykana jest gałąź:

```text
main
```

Na nowych gałęziach można wykonywać eksperymenty bez ryzyka uszkodzenia głównej wersji projektu.

---

# 3. Założenie konta GitHub

1. Otwórz stronę:

   https://github.com

2. Kliknij przycisk:

   ```text
   Sign Up
   ```

3. Podaj:
   - adres e-mail,
   - hasło,
   - nazwę użytkownika.

4. Potwierdź adres e-mail.

5. Zaloguj się do serwisu.

---

# 4. Utworzenie repozytorium potrzebnego do uruchomienia Codespace

Repozytorium zostanie wykorzystane wyłącznie do uruchomienia środowiska GitHub Codespaces.

1. Kliknij:

   ```text
   New Repository
   ```

2. Podaj nazwę:

   ```text
   laboratorium-git
   ```

3. Pozostaw ustawienie:

   ```text
   Public
   ```

4. Zaznacz:

   ```text
   Add README file
   ```

5. Kliknij:

   ```text
   Create Repository
   ```

---

# 5. Uruchomienie GitHub Codespace

1. Wejdź do utworzonego repozytorium.

2. Kliknij przycisk:

   ```text
   Code
   ```

3. Otwórz zakładkę:

   ```text
   Codespaces
   ```

4. Kliknij:

   ```text
   Create codespace on main
   ```

Po kilku chwilach otworzy się środowisko Visual Studio Code działające w przeglądarce internetowej.

---

# 6. Otworzenie terminala

Z górnego menu wybierz:

```text
Terminal → New Terminal
```

lub użyj skrótu:

```text
Ctrl + `
```

Powinien zostać otwarty terminal systemu Linux.

---

# 7. Utworzenie nowego repozytorium Git

Sprawdź aktualny katalog:

```bash
pwd
```

Przejdź do katalogu roboczego:

```bash
cd /workspaces
```

Utwórz nowy katalog projektu:

```bash
mkdir git-laboratorium
```

Przejdź do niego:

```bash
cd git-laboratorium
```

Utwórz repozytorium Git:

```bash
git init
```

Przykładowy wynik:

```text
Initialized empty Git repository in ...
```

W tym momencie powstało lokalne repozytorium Git.

---

# 8. Sprawdzenie stanu repozytorium

Wykonaj polecenie:

```bash
git status
```

Przykładowy wynik:

```text
On branch main

No commits yet

nothing to commit
```

Repozytorium istnieje, ale nie zawiera jeszcze żadnego commita.

---

# 9. Utworzenie pierwszego pliku

Utwórz plik:

```bash
touch notatka.txt
```

Dodaj zawartość:

```bash
echo "Moj pierwszy plik w repozytorium Git" > notatka.txt
```

Wyświetl zawartość:

```bash
cat notatka.txt
```

---

# 10. Sprawdzenie zmian

Wpisz:

```bash
git status
```

Przykładowy wynik:

```text
Untracked files:
    notatka.txt
```

Git zauważył nowy plik, ale jeszcze go nie śledzi.

---

# 11. Dodanie pliku do Staging Area

Dodaj plik:

```bash
git add notatka.txt
```

Sprawdź ponownie stan repozytorium:

```bash
git status
```

Przykładowy wynik:

```text
Changes to be committed
```

Oznacza to, że plik znajduje się już w Staging Area i jest gotowy do zapisania w historii projektu.

---

# 12. Utworzenie pierwszego commita

Wykonaj:

```bash
git commit -m "Dodano plik notatka.txt"
```

Przykładowy wynik:

```text
[main abc1234] Dodano plik notatka.txt
```

Powstał pierwszy commit.

---

# 13. Wyświetlenie historii zmian

Pełna historia:

```bash
git log
```

Historia skrócona:

```bash
git log --oneline
```

Przykład:

```text
abc1234 Dodano plik notatka.txt
```

---

# 14. Wprowadzenie zmian do istniejącego pliku

Dopisz nową linię:

```bash
echo "Druga linia tekstu" >> notatka.txt
```

Wyświetl zawartość:

```bash
cat notatka.txt
```

Powinieneś zobaczyć:

```text
Moj pierwszy plik w repozytorium Git
Druga linia tekstu
```

---

# 15. Sprawdzenie zmodyfikowanego pliku

Wykonaj:

```bash
git status
```

Git poinformuje, że plik został zmodyfikowany.

---

# 16. Dodanie zmian do Staging Area

Dodaj zmiany:

```bash
git add .
```

Polecenie dodaje wszystkie zmienione pliki znajdujące się w bieżącym katalogu.

Sprawdź stan:

```bash
git status
```

---

# 17. Utworzenie drugiego commita

Wykonaj:

```bash
git commit -m "Dodano druga linie tekstu"
```

---

# 18. Wyświetlenie historii commitów

Polecenie:

```bash
git log --oneline
```

Przykładowy wynik:

```text
dfe9210 Dodano druga linie tekstu
abc1234 Dodano plik notatka.txt
```

---

# 19. Utworzenie nowej gałęzi

Utwórz gałąź:

```bash
git branch funkcja
```

Sprawdź gałęzie:

```bash
git branch
```

Przykład:

```text
funkcja
* main
```

Gwiazdką oznaczona jest aktualna gałąź.

---

# 20. Przełączenie się na nową gałąź

Wykonaj:

```bash
git switch funkcja
```

Sprawdź:

```bash
git branch
```

Przykład:

```text
* funkcja
  main
```

---

# 21. Modyfikacja pliku na nowej gałęzi

Dodaj kolejną linię:

```bash
echo "Zmiana wykonana w galezi funkcja" >> notatka.txt
```

Wyświetl zawartość:

```bash
cat notatka.txt
```

---

# 22. Utworzenie nowego pliku

Wykonaj:

```bash
touch opis.txt
```

Dodaj zawartość:

```bash
echo "Plik utworzony na galezi funkcja" > opis.txt
```

---

# 23. Sprawdzenie zmian

```bash
git status
```

Powinieneś zobaczyć:

- zmodyfikowany plik `notatka.txt`,
- nowy plik `opis.txt`.

---

# 24. Dodanie zmian do Staging Area

Wykonaj:

```bash
git add .
```

Sprawdź:

```bash
git status
```

---

# 25. Commit na nowej gałęzi

Wykonaj:

```bash
git commit -m "Rozwoj funkcji"
```

---

# 26. Analiza historii

Wykonaj:

```bash
git log --oneline
```

Powinien pojawić się nowy commit.

---

# 27. Powrót do gałęzi głównej

Przełącz się:

```bash
git switch main
```

---

# 28. Sprawdzenie zawartości plików

Wyświetl plik:

```bash
cat notatka.txt
```

Zauważ, że zmiana utworzona na gałęzi `funkcja` nie jest jeszcze widoczna.

Gałęzie przechowują własne wersje plików.

---

# 29. Scalanie gałęzi

Wykonaj:

```bash
git merge funkcja
```

Przykładowy rezultat:

```text
Fast-forward
```

lub

```text
Merge made by ...
```

---

# 30. Sprawdzenie efektu scalenia

Wyświetl plik:

```bash
cat notatka.txt
```

Tym razem powinieneś zobaczyć również tekst dodany na gałęzi `funkcja`.

Sprawdź obecność nowego pliku:

```bash
ls
```

Powinien być widoczny:

```text
opis.txt
```

---

# 31. Wyświetlenie pełnej historii projektu

Wykonaj:

```bash
git log --oneline --graph
```

Przykładowy wynik:

```text
* 7f31a12 Rozwoj funkcji
* dfe9210 Dodano druga linie tekstu
* abc1234 Dodano plik notatka.txt
```

---

# Podsumowanie

Podczas ćwiczenia wykorzystano następujące polecenia:

```bash
git init
git status
git add
git commit
git log
git branch
git switch
git merge
```

Uczeń poznał pełny przepływ pracy:

```text
Tworzenie plików
        │
        ▼
Working Directory
        │
 git add
        ▼
Staging Area
        │
 git commit
        ▼
Historia projektu
        │
        ▼
Gałęzie i scalanie zmian
```

Po wykonaniu ćwiczenia powinieneś rozumieć różnicę pomiędzy:

- katalogiem roboczym (Working Directory),
- obszarem przygotowania zmian (Staging Area),
- commitem,
- gałęzią (branch),
- scalaniem gałęzi (merge),
- lokalnym repozytorium Git.