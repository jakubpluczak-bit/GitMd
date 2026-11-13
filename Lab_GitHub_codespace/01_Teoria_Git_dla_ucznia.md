# Git w terminalu — teoria dla ucznia

Ten tekst wyjaśnia **proces**: jak powstaje lokalne repozytorium, jak się nim zarządza i jak je kończy.  
Czytaj spokojnie. Nie musisz zapamiętać wszystkiego od razu — wracaj do fragmentów, gdy coś w ćwiczeniu przestanie być jasne.

Na lekcji pracujesz w **prawdziwym terminalu**. Środowisko (na przykład komputer w chmurze) jest tylko miejscem pracy.  
**Przedmiotem nauki jest Git** — program, który zapisuje historię zmian w projekcie.

---

## Jak korzystać z tego materiału (UDL)

Możesz uczyć się na kilka sposobów:

1. **Czytając od początku do końca** — zobaczysz cały cykl życia repozytorium.
2. **Patrząc najpierw na schematy** — potem wróć do wyjaśnień słownych.
3. **Szukając odpowiedzi na pytanie** — użyj spisu treści poniżej i otwórz tylko potrzebną część.
4. **Opowiadając sobie na głos** — po każdym rozdziale dokończ zdanie: „Właśnie zrozumiałem, że…”.

Jeśli jakieś słowo jest nowe, zatrzymaj się przy definicji. Nie pomijaj jej „na później” — w Gicie nazwy oznaczają konkretne miejsca i etapy pracy.

### Spis treści

1. Po co jest Git  
2. Trzy różne rzeczy: Git, serwis hostingowy, środowisko pracy  
3. Co to jest repozytorium  
4. Trzy miejsca, w których „żyją” zmiany  
5. Proces tworzenia lokalnego repozytorium  
6. Proces zarządzania zmianami (codzienny przepływ)  
7. Gałęzie — równoległe linie rozwoju  
8. Scalanie — łączenie linii rozwoju  
9. Kończenie cyklu — usunięcie repozytorium  
10. Cały proces w jednym przebiegu  
11. Słowniczek  

---

## 1. Po co jest Git

Gdy tworzysz stronę, skrypt albo notatkę w projekcie, pliki zmieniają się wiele razy. Bez kontroli wersji łatwo:

- nadpisać działającą wersję złą zmianą,
- nie pamiętać, co zostało zmienione wczoraj,
- bać się eksperymentować, bo „może zepsuję całość”.

**Git zapisuje historię projektu jako kolejne punkty kontrolne.**  
Każdy punkt kontrolny (commit) mówi w praktyce: „w tej chwili projekt wyglądał tak”.

Dzięki temu możesz:

- wracać do wcześniejszej, działającej wersji,
- porównywać, co się zmieniło,
- rozwijać pomysł obok stabilnej wersji (na gałęzi),
- łączyć sprawdzone zmiany z powrotem do głównej linii.

Git **nie zastępuje myślenia**. On zapisuje decyzje, które Ty podejmujesz: *które zmiany są gotowe*, *jak je nazwać*, *która linia rozwoju jest aktywna*.

---

## 2. Trzy różne rzeczy: Git, serwis hostingowy, środowisko pracy

Na lekcji mogą pojawić się trzy nazwy. To **nie to samo**.

| Nazwa | Czym jest | Rola na tej lekcji |
|---|---|---|
| **Git** | Program do kontroli wersji, obsługiwany w terminalu | Główny przedmiot nauki |
| **Serwis hostingowy** (np. GitHub) | Miejsce na konta i zdalne kopie projektów w internecie | Pomaga uruchomić środowisko; nie jest celem ćwiczenia |
| **Środowisko pracy** (np. edytor w chmurze z terminalem) | Komputer, na którym wpisujesz polecenia | „Sala komputerowa” na czas lekcji |

**Ważne:**  
Możesz nauczyć się lokalnego Gita nawet wtedy, gdy projekt **nie jest wysyłany** do internetu i **nie musi przetrwać** po lekcji.  
Historia powstaje najpierw **u Ciebie lokalnie**, w katalogu projektu.

---

## 3. Co to jest repozytorium

**Repozytorium** to katalog projektu, w którym Git prowadzi historię zmian.

Sam katalog z plikami (np. `index.html`, notatka tekstowa) **nie jest jeszcze** repozytorium Gita.  
Staje się nim dopiero wtedy, gdy Git utworzy w nim swoją „pamięć techniczną” — ukryty katalog metadanych.

Ten ukryty katalog zwykle nazywa się:

```text
.git
```

W środku Git przechowuje informacje potrzebne do historii.  
Ty na co dzień **nie edytujesz** zawartości `.git` ręcznie. Pracujesz na plikach projektu, a Git aktualizuje historię na Twoje polecenia.

### Repozytorium lokalne

Na tej lekcji tworzysz **repozytorium lokalne**:

- istnieje w katalogu na komputerze / w środowisku lekcyjnym,
- historia jest dostępna przez polecenia Gita w terminalu,
- nie musi być powiązane z kopią w internecie,
- może zostać usunięte po ćwiczeniu.

---

## 4. Trzy miejsca, w których „żyją” zmiany

To najważniejszy model w podstawach Gita.  
Zanim coś „zapiszemy w historii”, zmiana przechodzi przez etapy.

### 4.1. Katalog roboczy (Working Directory)

To pliki, które widzisz i edytujesz teraz.

Gdy dopiszesz linię do pliku albo utworzysz nowy plik:

- zmiana istnieje w katalogu roboczym,
- **historia Gita jeszcze o niej nie wie** jako o zapisanym punkcie kontrolnym,
- Git może jedynie zauważyć, że coś się zmieniło lub pojawiło.

### 4.2. Obszar przygotowania (Staging Area)

To miejsce przejściowe: **wybrane** zmiany, które mają wejść do następnego zapisu historii.

Wyobraź sobie koszyk:

- w katalogu roboczym leży wiele zmian,
- do koszyka wkładasz tylko te, które chcesz zapisać razem,
- reszta może poczekać.

Dzięki temu jeden zapis historii nie musi obejmować wszystkiego, co akurat jest niedokończone.

### 4.3. Historia projektu (commity)

**Commit** to zapisany punkt kontrolny.

Typowy commit zawiera między innymi:

- identyfikator (unikalny „numer” zapisu),
- autora,
- datę,
- opis (krótka informacja, *co* i *po co* zostało zapisane),
- stan plików objętych tym zapisem.

Commit nie jest „zapisaniem pliku na dysku” w zwykłym sensie edytora.  
Plik mogłeś zapisać w edytorze wcześniej. Commit oznacza: **ta wybrana wersja zmian wchodzi do historii projektu**.

### Schemat przepływu

```text
  Edytujesz pliki
         │
         ▼
 Katalog roboczy  ──(wybierasz zmiany)──►  Staging Area  ──(zapisujesz punkt)──►  Historia (commit)
```

Zapamiętaj kolejność sensowną dydaktycznie:

1. najpierw zmiana w pliku,
2. potem świadomy wybór zmian do zapisu,
3. na końcu zapis punktu w historii.

Pomijanie środkowego kroku „w głowie” (nawet jeśli kiedyś poznasz skróty) utrudnia zrozumienie, **co dokładnie** trafia do historii.

---

## 5. Proces tworzenia lokalnego repozytorium

Tworzenie repozytorium to nie jedna magiczna czynność. To krótki proces.

### Krok 1. Miejsce na projekt

Wybierasz / tworzysz katalog, w którym będą pliki ćwiczenia.  
To zwykły katalog systemu plików.

### Krok 2. Inicjalizacja Gita

W tym katalogu uruchamiasz inicjalizację repozytorium.  
Wtedy Git:

- przygotowuje ukrytą pamięć historii (`.git`),
- ustawia startową linię rozwoju (gałąź startowa, często nazywaną `main`),
- jeszcze **nie ma** commitów, bo nie zapisano żadnego punktu kontrolnego.

Po inicjalizacji możesz sprawdzić stan. Typowa informacja brzmi w praktyce:

- jesteś na gałęzi startowej,
- nie ma jeszcze commitów,
- nie ma przygotowanych zmian do zapisu  
  (albo Git widzi już pliki, jeśli coś utworzyłeś wcześniej).

### Krok 3. Pierwsza zawartość

Tworzysz plik lub pliki projektu.  
Na tym etapie są to zwykle pliki **niesledzone** (untracked): Git je widzi jako nowe, ale jeszcze ich nie prowadzi w historii.

### Krok 4. Pierwszy zapis historii

Aby powstał pierwszy commit:

1. wybierasz plik(i) do obszaru przygotowania,
2. tworzysz commit z opisem.

Od tego momentu projekt ma już **pierwszy punkt kontrolny**.  
Repozytorium „żyje” — ma historię.

---

## 6. Proces zarządzania zmianami (codzienny przepływ)

Zarządzanie repozytorium to powtarzalna pętla.

### 6.1. Sprawdź stan, zanim coś zrobisz

Stan repozytorium odpowiada na pytania:

- na której gałęzi jestem?
- co jest zmienione w katalogu roboczym?
- co jest już wybrane do następnego commita?
- czy są nowe pliki, których Git jeszcze nie śledzi?

**Dobra zasada:** najpierw stan, potem decyzja, potem polecenie zmieniające historię.

### 6.2. Wprowadź zmianę w plikach

Edytujesz istniejący plik albo tworzysz nowy.  
To nadal katalog roboczy.

### 6.3. Zobacz, co Git zauważył

Ponownie sprawdzasz stan (a gdy trzeba — różnice w treści).  
Celem jest świadomość: *co dokładnie zamierzam zapisać?*

### 6.4. Wybierz zmiany do zapisu

Przenosisz wybrane zmiany do obszaru przygotowania.  
To moment decyzji jakościowej: „te zmiany tworzą sensowną całość”.

### 6.5. Zapisz punkt kontrolny

Tworzysz commit i nadajesz mu opis.  
Dobry opis mówi przyszłemu sobie (i innym), **jaka decyzja** została zapisana, a nie tylko „poprawki”.

### 6.6. Przejrzyj historię

Historia pokazuje kolejne commity.  
To sprawdzian: czy zapis naprawdę powstał i czy opis jest czytelny.

Ta pętla może powtórzyć się wiele razy w jednym projekcie.

---

## 7. Gałęzie — równoległe linie rozwoju

**Gałąź (branch)** to linia rozwoju projektu.

Najprostszy obraz:

- gałąź główna (`main`) trzyma wersję uznaną za bazową,
- nowa gałąź pozwala rozwijać pomysł **obok**, bez natychmiastowego mieszania go z bazą.

### Po co tworzy się gałąź

Żeby:

- eksperymentować bezpieczniej,
- oddzielić temat pracy (np. „nowa funkcja”) od stabilnej linii,
- móc wrócić do bazy i zobaczyć, że zmian z eksperymentu tam jeszcze nie ma.

### Jak wygląda praca na gałęzi w procesie

1. Masz już historię na gałęzi głównej.  
2. Tworzysz nową gałąź od aktualnego stanu.  
3. Przełączasz się na nią.  
4. Wprowadzasz zmiany, wybierasz je, commit’ujesz.  
5. Historia tej gałęzi rośnie do przodu.  
6. Gdy wrócisz na gałąź główną **przed scaleniem**, nie zobaczysz tam jeszcze tych commitów.

To nie jest błąd. To właśnie rozdzielenie linii rozwoju.

```text
main:     A --- B
                 \
funkcja:          C --- D
```

W powyższym szkicu `C` i `D` istnieją na linii `funkcja`, a `main` na razie kończy się na `B`.

---

## 8. Scalanie — łączenie linii rozwoju

**Scalanie (merge)** wciąga zmiany z jednej gałęzi do drugiej.

Typowy proces na poziomie podstaw:

1. Przełączasz się na gałąź **docelową** (np. główną).  
2. Uruchamiasz scalenie z gałęzi źródłowej (np. z gałęzi funkcji).  
3. Sprawdzasz pliki i historię: czy oczekiwane zmiany są obecne.

### Co warto rozumieć na start

Jeśli gałąź główna nie dostała w międzyczasie innych, rozbieżnych commitów, scalenie często przebiega jako proste „przesunięcie do przodu” historii (fast-forward).  
To oznacza: główna linia może po prostu dogonić gałąź, na której pracowałeś.

Później poznasz sytuacje trudniejsze (konflikty), gdy obie linie zmieniły te same miejsca inaczej.  
Na pierwszym laboratorium ważne jest coś innego: **zrozumieć, że gałęzie mają osobne historie, a merge jest świadomym połączeniem**.

Po udanym scaleniu:

- pliki na gałęzi docelowej zawierają wciągnięte zmiany,
- historia pokazuje, że praca z drugiej linii jest już częścią linii docelowej.

---

## 9. Kończenie cyklu — usunięcie repozytorium

Repozytorium lokalne można świadomie zakończyć.

Usunięcie katalogu projektu (wraz z ukrytym katalogiem historii) oznacza:

- koniec lokalnego repozytorium ćwiczeniowego,
- brak dalszej lokalnej historii tego projektu,
- domknięcie cyklu: **utworzenie → zarządzanie → usunięcie**.

Na lekcji to jest zamierzone.  
Celem nie jest „posiadanie repozytorium na zawsze”, tylko **zrozumienie procesu zarządzania nim**.

Zanim coś usuniesz:

1. upewnij się, że jesteś **poza** katalogiem, który kasujesz,
2. usuń właściwy katalog ćwiczeniowy,
3. sprawdź listę katalogów, czy projekt naprawdę zniknął.

Usuwanie to też część odpowiedzialnej pracy z repozytorium: wiesz, gdzie jest historia i kiedy przestaje istnieć.

---

## 10. Cały proces w jednym przebiegu

Poniżej jest mapa całego cyklu, który ćwiczysz na laboratorium.

```text
1. Przygotuj katalog projektu
2. Zainicjalizuj lokalne repozytorium Git
3. Utwórz / edytuj pliki (katalog roboczy)
4. Sprawdź stan
5. Wybierz zmiany do obszaru przygotowania
6. Zapisz commit (punkt historii)
7. Przeglądaj historię
8. (Opcjonalnie powtarzaj 3–7)
9. Utwórz gałąź i przełącz się na nią
10. Pracuj i commit’uj na gałęzi
11. Wróć na gałąź docelową
12. Scal zmiany
13. Zweryfikuj efekt (pliki + historia)
14. Usuń lokalne repozytorium ćwiczeniowe
```

Jeśli umiesz opowiedzieć ten przebieg własnymi słowami, rozumiesz podstawę zarządzania repozytorium — nawet zanim wszystkie polecenia wejdą w nawyk.

---

## 11. Słowniczek

| Pojęcie | Znaczenie |
|---|---|
| **Git** | System kontroli wersji działający lokalnie (tu: z terminala) |
| **Repozytorium** | Katalog projektu z historią Gita |
| **`.git`** | Ukryty katalog metadanych historii |
| **Katalog roboczy** | Aktualne pliki, które edytujesz |
| **Staging Area** | Wybrane zmiany czekające na commit |
| **Commit** | Zapisany punkt kontrolny historii |
| **Gałąź (branch)** | Linia rozwoju projektu |
| **Gałąź główna** | Bazowa linia (często `main`) |
| **Przełączenie gałęzi** | Zmiana aktywnej linii rozwoju |
| **Scalanie (merge)** | Włączenie historii jednej gałęzi do drugiej |
| **Stan repozytorium** | Informacja: gdzie jesteś i co jest zmienione / przygotowane |
| **Historia** | Lista commitów w czasie |

---

## Na koniec

Git nagradza uważność, nie pośpiech.

Zanim wykonasz kolejną czynność, zadaj sobie trzy pytania:

1. **Gdzie jestem?** (katalog, gałąź)  
2. **Co jest zmienione, a co już wybrane do zapisu?**  
3. **Jaką decyzję chcę zapisać w historii — albo której linii dotyczy moja praca?**

Gdy odpowiesz na te pytania, polecenia w terminalu przestają być „zaklęciami” i stają się narzędziami procesu, który rozumiesz.
