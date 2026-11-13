# Karty pracy: pierwsze spotkanie z repozytorium w terminalu

**Charakter:** ćwiczenie uczące (to **nie** sprawdzian i **nie** ocena)  
**Kontekst:** powtórka spiralna — GitHub znasz z przeglądarki; dziś przenosisz pracę do terminala  
**Czas:** ok. 10–15 min wejście do Codespace + ok. 75 min ścieżka Git (A–E)  
**Forma:** GitHub Codespaces = VS Code w przeglądarce + terminal  
**Materiały obok:** `01_Teoria_Git_dla_ucznia.md`, `02_Pomoc_mapa_decyzji_Git.md`, `04_Sciaga_skladni_terminal_Git.md`

### Podział pracy: VS Code + terminal

| W VS Code (edytor) | W terminalu |
|---|---|
| tworzenie i edycja treści plików | orientacja: gdzie jestem, katalogi (`pwd`, `cd`, `mkdir`, `ls`) |
| wygodny podgląd plików | **wszystkie decyzje Gita** (`init`, `status`, `add`, `commit`, `log`, gałęzie, `merge`) |
| ewentualnie oglądanie konfliktu przy ścieżce + | sprawdzanie efektów i domknięcie (usuń katalog ćwiczenia) |

**Zasada na dziś:** treść plików możesz robić w edytorze; historii projektu **nie prowadzisz klikaniem** w panelu Source Control — ćwiczysz ją w terminalu.

---

## Zanim zaczniesz (2–3 min)

To Wasze **pierwsze spokojne spotkanie** z repozytorium prowadzonym z terminala.  
Wolno się mylić, wolno pytać, wolno wracać do poprzedniego etapu.

Masz już konto GitHub i doświadczenie z zarządzaniem w **przeglądarce**.  
Codespaces możesz znać słabo albo wcale — **Karta 0** przeprowadzi Cię do terminala krok po kroku.

**Cel lekcji (nauka, nie test):** przećwiczyć cykl  
**inicjalizacja repo → zarządzanie zmianami → gałęzie → scalanie → domknięcie.**

Później (osobno) przyjdzie zadanie „sprawdź się” i ewentualna ocena.  
**Dziś liczy się próbowanie ze zrozumieniem**, nie perfekcja.

### Jak korzystać z kart (UDL)

- Pracuj **etapami**. Po każdym etapie odhacz checklistę — to Twój postęp, nie „zaliczenie”.
- Jeśli utkniesz: najpierw **mapa decyzji** (co zrobić), potem **ściąga składni** (jak wpisać), potem teoria, potem pytanie do nauczyciela.  
  Ściąga ma **inne przykłady** niż zadania — nie kopiuj jej 1:1 jako rozwiązania karty.
- Masz **ścieżkę podstawową** (na lekcję) i **ścieżkę +** (bonus / dom, gdy będziesz gotowy).
- Tempo może być różne. Lepiej wolniej i ze zrozumieniem niż szybko „na ślepo”.

### Ważne rozróżnienie (przeczytaj raz)

| Co | Po co |
|---|---|
| **Repozytorium nośnikowe** na GitHubie | Tylko po to, żeby **uruchomić Codespace** (komputer w chmurze) |
| **Repozytorium ćwiczeniowe** w terminalu | Tu ćwiczysz: tworzysz je **sam od zera** (`init`) |

Dziś pracujesz w terminalu, w **nowym katalogu**, który sam utworzysz.

---

# KARTA 0 — Wejście do GitHub Codespaces  
**Czas orientacyjny:** 10–15 min · **Na lekcję** (jeśli Codespace nie jest jeszcze otwarty)

## Po co ten etap

W szkole nie pracujemy na lokalnie zainstalowanym Gicie.  
Codespace = **gotowy komputer z terminalem w przeglądarce**.  
To tylko „sala komputerowa”. Dziś uczymy się Gita w terminalu — Codespace jest tylko wejściem.

## Zadanie 0.1. Zaloguj się

1. Wejdź na [https://github.com](https://github.com).
2. Zaloguj się na swoje konto.

**Check:** widać Twój avatar / menu konta.

## Zadanie 0.2. Utwórz repozytorium nośnikowe (jeśli jeszcze nie masz)

Jeśli nauczyciel podał gotowe repo do Codespace — pomiń tworzenie i przejdź do 0.3.

W przeciwnym razie:

1. Kliknij **New repository** (lub **+** → **New repository**).
2. Podaj nazwę, np. `laboratorium-git` (może być inna, byle zapamiętana).
3. Ustaw widoczność: **Public** (najprostsze na lekcję).
4. Zaznacz opcję dodania pliku **README** (żeby repo nie było całkiem puste).
5. Kliknij **Create repository**.

**Notatka:** nazwa mojego repo nośnikowego: `……………………………………`

## Zadanie 0.3. Uruchom Codespace

1. Wejdź na stronę swojego repozytorium nośnikowego.
2. Kliknij zielony przycisk **Code**.
3. Otwórz zakładkę **Codespaces** (obok „Local”).
4. Kliknij **Create codespace on main**  
   (jeśli Codespace już istnieje: **Open in …** / wybierz istniejący).
5. Poczekaj na załadowanie edytora w przeglądarce (pierwszy raz może potrwać kilka minut).

**Check:** widzisz interfejs podobny do VS Code (pliki z lewej, obszar edytora).

### Jeśli coś wygląda inaczej

| Objaw | Co zrobić |
|---|---|
| Nie widzę zakładki Codespaces | Upewnij się, że jesteś zalogowany; odśwież stronę; poproś nauczyciela |
| Tworzenie Codespace się dłuży | Poczekaj; przy pierwszym starcie to normalne |
| Limit / komunikat o braku możliwości | Zgłoś nauczycielowi (limity konta / organizacji) |
| Otworzyło się złe repo | Sprawdź nazwę repo na górze strony i wróć do właściwego |

## Zadanie 0.4. Otwórz terminal w Codespace

1. W górnym menu wybierz **Terminal → New Terminal**  
   albo użyj skrótu **Ctrl + \`** (Control + tylda).
2. Upewnij się, że na dole ekranu widać panel terminala z zachętą systemową (prompt).

**Check:** możesz wpisywać polecenia i naciskać Enter.

## Zadanie 0.5. Zapamiętaj zasadę miejsca pracy

Po starcie Codespace często jesteś już w katalogu sklonowanego repo **nośnikowego**.  
To **nie** jest jeszcze Twoje repo ćwiczeniowe.

Na Karcie A:

- wyjdziesz / przejdziesz do miejsca na nowy katalog,
- utworzysz **własny** katalog,
- dopiero tam zrobisz inicjalizację Gita od zera.

### Checklista 0

- [ ] Jestem zalogowany na GitHub  
- [ ] Mam repo nośnikowe (własne lub wskazane)  
- [ ] Codespace jest otwarty w przeglądarce  
- [ ] Terminal jest otwarty  
- [ ] Wiem, że właściwe repo ćwiczeniowe utworzę dopiero na Karcie A  

**Jeśli utkniesz na Karcie 0:** nie zaczynaj Karty A „na siłę”. To wejście do sali — bez terminala nie ma ćwiczenia.

---

# KARTA A — Start i inicjalizacja od zera  
**Czas orientacyjny:** 15 min · **Na lekcję**

## Po co ten etap

Zwykły katalog z plikami to jeszcze nie repozytorium Gita.  
Inicjalizacja (`init`) uruchamia lokalną historię projektu.  
Ćwiczysz to **od zera**, bo później ta umiejętność wróci (m.in. przy przygotowaniu do INF.04) — dziś po prostu poznajesz ten moment spokojnie.

## Zadanie A1. Orientacja w terminalu

1. Upewnij się, że terminal w Codespace jest aktywny (Karta 0).
2. Sprawdź, w jakim katalogu jesteś.
3. Przejdź do miejsca, w którym możesz utworzyć **nowy** katalog ćwiczeniowy  
   (często katalog nadrzędny workspace, np. poziom `/workspaces` — sprawdź u siebie).

**Notatka ucznia:**  
Jestem na starcie w katalogu: `……………………………………`  
To katalog repo nośnikowego? (tak/nie/nie wiem): `……………………………………`  
Przechodzę do: `……………………………………`

## Zadanie A2. Katalog projektu

1. Utwórz nowy katalog na ćwiczenie (wybierz sensowną nazwę).
2. Wejdź do niego.
3. Sprawdź, że jesteś **w środku** tego katalogu.

**Check:** lista plików jest pusta (lub bez historii Gita).

## Zadanie A3. Inicjalizacja repozytorium (od zera)

1. Zainicjalizuj lokalne repozytorium Git tak, aby startowa gałąź nazywała się `main`.
2. Sprawdź stan repozytorium.

**Odpowiedz własnymi słowami:**

- Co powstało po inicjalizacji?  
  `………………………………………………………………`
- Czy masz już jakiś commit? Dlaczego tak / nie?  
  `………………………………………………………………`

### Checklista A

- [ ] Mam własny katalog ćwiczeniowy  
- [ ] Jestem w jego wnętrzu  
- [ ] Repo zostało zainicjalizowane **przeze mnie** (nie korzystam z cudzej historii jako startu)  
- [ ] `status` potwierdza gałąź startową i brak commitów (na tym etapie)

**Jeśli utkniesz:** nie idź dalej „na ślepo”. Wróć do mapy decyzji → „Chcę utworzyć repozytorium”.

---

# KARTA B — Pliki, staging, commit, historia  
**Czas orientacyjny:** 20 min · **Na lekcję**

## Po co ten etap

Tu odkrywasz ważną różnicę: *zmiana w pliku ≠ zapis w historii*.  
Ćwiczysz spokojny przepływ: katalog roboczy → wybór zmian → commit.

## Zadanie B1. Pierwszy plik

1. W **VS Code** utwórz plik tekstowy z notatką o projekcie (treść **własnymi słowami**) i zapisz go.  
   (Jeśli wolisz, możesz też utworzyć plik w terminalu — obie drogi są OK.)
2. W terminalu sprawdź, że plik widać na liście katalogu; możesz też podejrzeć treść.
3. Sprawdź stan repozytorium **w terminalu**.

**Pytanie:** Jak Git opisuje ten plik przed dodaniem do obszaru przygotowania?  
`………………………………………………………………`

## Zadanie B2. Pierwszy commit

1. Dodaj plik do obszaru przygotowania.
2. Sprawdź stan (co się zmieniło w komunikacie?).
3. Utwórz commit z opisem, który **Ty** wymyślisz.
4. Wyświetl historię w skróconej postaci.

**Notatka:** treść opisu commita: `……………………………………`

## Zadanie B3. Druga zmiana

1. W **VS Code** dopisz kolejną linię do tego samego pliku i zapisz.
2. W terminalu (wskazane) podejrzyj różnicę przed dodaniem.
3. Przygotuj zmiany i zapisz **drugi** commit **w terminalu**.
4. Ponownie przejrzyj historię w terminalu.

### Checklista B

- [ ] Mam co najmniej **2 commity**  
- [ ] Potrafię wskazać różnicę: plik zmieniony vs plik przygotowany vs zapisany w historii  
- [ ] Opisy commitów wymyśliłem sam  
- [ ] Umiem pokazać historię sobie na ekranie  

**Wystarczy na ten etap:** 2 commity — potem możesz iść do Karty C.

---

# KARTA C — Gałąź, praca równoległa, powrót  
**Czas orientacyjny:** 15 min · **Na lekcję**

## Po co ten etap

Gałąź to bezpieczna linia eksperymentu: możesz coś wypróbować obok wersji bazowej.

## Zadanie C1. Nowa gałąź

1. Utwórz gałąź tematyczną (nazwa po polsku lub angielsku — byle sensowna).
2. Wyświetl listę gałęzi.
3. Przełącz się na nową gałąź.

**Notatka:** nazwa gałęzi: `……………………………………`

## Zadanie C2. Praca na gałęzi

1. W **VS Code** zmień istniejący plik **oraz** dodaj nowy plik (zapisz oba).
2. W terminalu sprawdź stan.
3. Przygotuj zmiany i zapisz commit na tej gałęzi **w terminalu**.
4. Podejrzyj historię w terminalu.

## Zadanie C3. Powrót na `main` — obserwacja

1. Przełącz się na `main`.
2. Sprawdź zawartość plików / listę plików.

**Odpowiedz:**  
Czy zmiany z gałęzi tematycznej są już widoczne na `main`? Dlaczego?  
`………………………………………………………………`

### Checklista C

- [ ] Mam co najmniej 2 gałęzie  
- [ ] Commit tematyczny powstał **na gałęzi tematycznej**  
- [ ] Po powrocie na `main` rozumiem, dlaczego efekt może być inny  

---

# KARTA D — Scalanie i weryfikacja  
**Czas orientacyjny:** 15 min · **Na lekcję**

## Po co ten etap

Merge to moment: „wciągam pracę z innej linii do linii docelowej”.  
Zanim scalasz, sprawdź, na której gałęzi stoisz — to częsty punkt pomyłki na początku.

## Zadanie D1. Merge

1. Upewnij się, że jesteś na gałęzi **docelowej** (`main`).
2. Scal gałąź tematyczną.
3. Zanotuj, jaki komunikat zobaczyłeś (własnymi słowami).

**Notatka:** `……………………………………`

## Zadanie D2. Weryfikacja efektu

1. Sprawdź treść plików (VS Code lub terminal).
2. W terminalu sprawdź, czy nowy plik jest obecny (`ls`).
3. W terminalu wyświetl historię (najlepiej z grafem, jeśli pamiętasz opcję).

### Checklista D

- [ ] Merge wykonany z poziomu `main`  
- [ ] Zmiany z gałęzi tematycznej są na `main`  
- [ ] Potrafię pokazać to w historii  

---

# KARTA E — Domknięcie cyklu  
**Czas orientacyjny:** 10 min · **Na lekcję**

## Po co ten etap

Kończysz lokalne repo świadomie i spokojnie.  
Ćwiczysz też ostrożność: kasujesz **właściwy** katalog projektu.

## Zadanie E1. Podsumowanie przed usunięciem

Dokończ zdania:

1. Repo utworzyłem przez: `……………………………………`  
2. Zmiany trafiały do historii dopiero po: `……………………………………`  
3. Gałąź była potrzebna, ponieważ: `……………………………………`  
4. Przed merge musiałem być na: `……………………………………`

## Zadanie E2. Usunięcie lokalnego repo ćwiczeniowego

1. Wyjdź z katalogu projektu.
2. Usuń katalog ćwiczeniowy.
3. Potwierdź, że katalog zniknął.

### Checklista E (koniec ścieżki podstawowej)

- [ ] Potrafię opowiedzieć cykl od `init` do usunięcia (własnymi słowami)  
- [ ] Lokalne repo ćwiczeniowe zostało usunięte  
- [ ] Czuję różnicę między klikaniem w GitHubie a pracą w terminalu  

---

# Co warto mieć za sobą po dzisiejszej lekcji

To nie jest lista do oceny — raczej „zdjęcie postępu”:

1. Wszedłem do Codespace i mam działający terminal (Karta 0).  
2. **Sam** zainicjalizowałem repo ćwiczeniowe od zera (osobno od repo nośnikowego).  
3. Zrobiłem co najmniej 2 commity.  
4. Utworzyłem gałąź, commit na niej, wróciłem, scaliłem.  
5. Potrafię krótko powiedzieć, czym różni się katalog roboczy / staging / commit.  
6. Domknąłem ćwiczenie usunięciem katalogu ćwiczeniowego.

Jeśli czegoś nie dokończysz dziś — OK. Zanotuj, na którym etapie stanąłeś, i wróć do tego później.  
Ścieżka + jest na dom / bonus, gdy ścieżka podstawowa już „siądzie”.

---

# ŚCIEŻKA + — Konflikt scalania  
**Bonus / praca domowa · nie na ocenę z tej lekcji**  
**Czas:** ok. 20–30 min poza ścieżką podstawową

## Po co

Czasem dwie linie zmieniają **to samo miejsce** inaczej.  
Git wtedy nie zgaduje za Ciebie — prosi o decyzję.  
To przydatne na później (także przy przygotowaniu do INF.04), ale **nie jest potrzebne**, żeby dzisiejsze pierwsze spotkanie z terminalem uznać za udane.

## Zasady bezpieczeństwa

- Rób to **po** ścieżce podstawowej (albo na nowym, czystym repo od `init`).
- Nie kasuj wszystkiego w panice — najpierw stan, potem decyzja.
- Korzystaj z mapy decyzji (diagnostyka), nie z kopiowania gotowca.

## Scenariusz + (sam prowadzisz)

1. Utwórz **nowe** lokalne repo od zera (znowu `init` — kolejna spokojna próba).  
2. Commit startowy z jednym plikiem tekstowym (np. jedna linia bazowa).  
3. Utwórz gałąź tematyczną.  
4. Na gałęzi tematycznej zmień **tę samą linię** i zrób commit.  
5. Wróć na `main` i zmień **tę samą linię inaczej**, zrób commit.  
6. Spróbuj scalić — powinien pojawić się konflikt.  
7. Odczytaj komunikaty / oznaczenia konfliktu w pliku.  
8. Świadomie wybierz ostateczną treść (albo połącz sensownie).  
9. Domknij konflikt zgodnie z procesem Gita (przygotowanie + commit kończący merge).  
10. Sprawdź historię i treść pliku.  
11. Na końcu możesz usunąć to repo.

### Checklista ścieżki +

- [ ] Konflikt pojawił się w kontrolowany sposób  
- [ ] Rozumiem, że konflikt = prośba o decyzję, nie „zepsuty Git”  
- [ ] Potrafię opowiedzieć: co zrobiłem na `main`, co na gałęzi, jak rozstrzygnąłem  

### Pytania do przemyślenia (dom)

1. Dlaczego konflikt nie powstał na lekcji w ścieżce podstawowej?  
2. Co musiałoby się wydarzyć, żeby merge nie był prostym fast-forward?  
3. Jak sprawdzić, że konflikt jest już rozwiązany?

---

## Notatka dla szybszych / wolniejszych (UDL)

| Jeśli… | Zrób tak |
|---|---|
| Pierwszy raz w Codespace i długo startuje | Dokończ Kartę 0 spokojnie; A–E ważniejsze niż bonus |
| Masz mniej czasu / utykasz | Domknij Karty A–E bez ścieżki + |
| Kończysz wcześniej | Zrób ścieżkę + albo powtórz A3+B na nowym katalogu „na czas” |
| Boisz się usunąć katalog | Poproś nauczyciela o kontrolę nazwy **przed** usunięciem |
| Mylą Ci się pojęcia | 5 minut teorii (rozdziały o 3 miejscach zmian + gałęzie), potem wróć do karty |
| Nie wiesz, czy jesteś w repo nośnikowym | Wróć do Karty 0.5 i A1 — najpierw orientacja katalogu |

---

## Czego te karty celowo nie robią

- nie są sprawdzianem ani arkuszem oceny,
- nie podają pełnych komend „do wklejenia” krok po kroku,
- nie zastępują późniejszego zadania „sprawdź się”.

Dziś: **pierwsze spotkanie z repo w terminalu** — od inicjalizacji, spokojnie, ze sprawdzaniem stanu.
