# Pomoc: mapa decyzji Git (dla ucznia)

To **nie jest klucz z gotowymi komendami do wklejenia**.  
To kompas: pomaga **myśleć**, zanim coś wpiszesz w terminal.

Jeśli nie wiesz, co zrobić — najpierw przejdź ścieżkę pytań.  
Dopiero potem dobierz polecenie z pamięci, z notatek z lekcji albo pytając nauczyciela.

---

## Jak korzystać (UDL)

Wybierz sposób, który Ci pasuje:

1. **Ścieżka awaryjna** — zacznij od sekcji „Zatrzymaj się i sprawdź orientację”.  
2. **Po celu** — otwórz tabelę „Chcę… → najpierw pomyśl”.  
3. **Po objawie** — zajrzyj do „Coś wygląda nie tak”.  
4. **Po procesie** — użyj checklisty cyklu życia na końcu.

Zasada tej pomocy:  
**najpierw pytanie i decyzja, potem komenda** — nigdy odwrotnie.

---

## Zatrzymaj się i sprawdź orientację

Zanim cokolwiek zmienisz w repozytorium, odpowiedz pisemnie (w głowie lub na kartce):

1. W jakim **katalogu** jestem?  
2. Czy to katalog **ćwiczeniowy**, czy tylko środowisko startowe?  
3. Na której **gałęzi** powinienem teraz być?  
4. Czy chcę tylko **obejrzeć stan**, czy już **zmienić historię**?

Jeśli na któreś pytanie nie umiesz odpowiedzieć — **nie zapisuj commita** i nie scalaj.  
Najpierw odzyskaj orientację (stan / lista plików / która gałąź jest aktywna).

---

## Rodziny działań (bez gotowców)

Poniżej są **rodzaje** działań.  
Dopisz samodzielnie konkretną składnię, którą poznajesz na lekcji.

| Jeśli Twoim celem jest… | Rodzina działania | Zanim to zrobisz, sprawdź… |
|---|---|---|
| Wiedzieć, gdzie jesteś w systemie plików | nawigacja katalogów | czy ścieżka wygląda na katalog ćwiczenia |
| Utworzyć miejsce na projekt | tworzenie katalogu + wejście do niego | czy nie tworzysz projektu „w środku” innego, przypadkowego miejsca |
| Zacząć lokalną historię Gita | inicjalizacja repozytorium | czy jesteś **wewnątrz** katalogu projektu |
| Zobaczyć, co Git myśli o plikach | odczyt stanu | czy patrzysz na właściwe repo |
| Zobaczyć treść różnicy w pliku | podgląd różnic | czy wiesz, który plik się zmienił |
| Wybrać zmiany do następnego zapisu | dodanie do obszaru przygotowania | czy na pewno te zmiany tworzą jedną sensowną całość |
| Zapisać punkt historii | utworzenie commita | czy coś jest przygotowane; czy opis mówi o decyzji, nie o „poprawkach w ogóle” |
| Zobaczyć dotychczasowe zapisy | odczyt historii | czy patrzysz na właściwą gałąź |
| Rozwinąć pracę obok wersji bazowej | utworzenie gałęzi | czy bazujesz na stanie, od którego naprawdę chcesz odgałęzić |
| Pracować na innej linii | przełączenie gałęzi | czy nie masz chaosu nieopisanych zmian, których nie rozumiesz |
| Wciągnąć pracę z innej linii | scalanie | czy jesteś na gałęzi **docelowej** |
| Zakończyć lokalne ćwiczenie | usunięcie katalogu projektu | czy jesteś **poza** katalogiem, który kasujesz |

Uzupełnij własną notatkę:

```text
Rodzina: ..............................
Polecenie, które do niej pasuje: ......
Składnia / opcje, które muszę pamiętać: ......
```

---

## Chcę… → najpierw pomyśl

### Chcę utworzyć repozytorium

Zapytaj siebie:

- Czy katalog projektu już istnieje?  
- Czy jestem **w środku** tego katalogu?  
- Czy chcę zacząć historię od gałęzi głównej o ustalonej nazwie?

Dopiero wtedy użyj inicjalizacji.  
Po niej od razu sprawdź stan: czy Git potwierdza puste jeszcze repo / gałąź startową.

### Chcę dodać nowy plik do historii

Kolejność myślenia:

1. Plik najpierw powstaje w katalogu roboczym.  
2. Stan powinien pokazać go jako niesledzony / nowy.  
3. Dopiero potem wybierasz go do obszaru przygotowania.  
4. Commit zapisuje decyzję „ten plik należy już do historii”.

Pytanie kontrolne:  
**Czy commit opisuje pojawienie się pliku, czy przypadkiem mieszam to z inną, niepowiązaną zmianą?**

### Chcę zapisać poprawkę w istniejącym pliku

Kolejność myślenia:

1. Zmiana treści.  
2. Podgląd: co konkretnie się zmieniło.  
3. Wybór do obszaru przygotowania.  
4. Commit z opisem **tej** poprawki.

Pytanie kontrolne:  
**Czy potrafę jednym zdaniem powiedzieć, jaka decyzja trafia do historii?**

### Chcę pracować „obok”, bez psucia wersji bazowej

Kolejność myślenia:

1. Czy baza ma już sensowny punkt startu (commit)?  
2. Tworzę osobną linię rozwoju.  
3. Przełączam się na nią.  
4. Dopiero wtedy wprowadzam eksperyment.  
5. Zapisuję commit **na tej** linii.

Pytanie kontrolne:  
**Gdy wrócę na linię bazową przed scaleniem, czy spodziewam się, że eksperymentu tam jeszcze nie będzie?**  
Jeśli tak — rozumiesz gałęzie.

### Chcę połączyć pracę z gałęzi z wersją bazową

Kolejność myślenia:

1. Najpierw upewnij się, że praca na gałęzi źródłowej jest zapisana w commitach.  
2. Przełącz się na gałąź **do której** chcesz wciągnąć zmiany.  
3. Dopiero wtedy scalaj.  
4. Sprawdź pliki i historię.

Pytanie kontrolne:  
**Czy na pewno stoję na gałęzi docelowej, a nie źródłowej?**

### Chcę zakończyć i usunąć lokalne repo

Kolejność myślenia:

1. Czy ćwiczenie jest domknięte (stan / historia / efekt scalenia)?  
2. Wyjdź z katalogu projektu.  
3. Usuń **właściwy** katalog ćwiczeniowy.  
4. Potwierdź listą katalogów, że zniknął.

Pytanie kontrolne:  
**Czy kasuję katalog ćwiczenia, a nie całe środowisko „w ciemno”?**

---

## Mini-szablony do myślenia (luki uzupełniasz Ty)

Możesz ćwiczyć składnię, **nie kopiując gotowca z karty zajęć**:

```text
sprawdzenie stanu:     git ................
wybór pliku:           git ................ nazwa_pliku
wybór wielu zmian:     git ................
zapis historii:        git ................ -m "................"
historia skrócona:     git ................
lista gałęzi:          git ................
przełączenie:          git ................ nazwa_galezi
scalanie:              git ................ nazwa_galezi
```

Zasada: jeśli nie potrafisz uzupełnić luki bez zaglądania w klucz ćwiczenia, wróć do teorii procesu albo zapytaj.  
Ściąga ma Cię doprowadzić do **rozumienia luk**, nie do ich omijania.

---

## Opis commita — jak myśleć, nie co wpisać

Zły nawyk: pisać zawsze to samo, „bo tak było w przykładzie”.

Zanim zatwierdzisz opis, sprawdź:

- Czy opis mówi **co** weszło do historii?  
- Czy mówi **dlaczego / jaki skutek** (choćby krótko)?  
- Czy pasuje do *tych* zmian, które są w obszarze przygotowania?

Przetestuj opis pytaniem:  
**Gdy za tydzień zobaczę tylko ten opis, czy odgadnę decyzję bez otwierania plików?**

---

## Coś wygląda „nie tak” — diagnostyka bez gotowca

| Obserwacja | Najpierw pomyśl | Czego NIE rób od razu |
|---|---|---|
| „Git nie widzi mojego pliku” | Czy jesteś w katalogu projektu? Czy plik naprawdę istnieje? | Panika + losowe zapisy historii |
| „Na serwisie w internecie nic nie ma” | Czy ta lekcja w ogóle wymaga wysyłania projektu? | Wymuszanie publikacji „na ślepo” |
| „Zniknęły zmiany po przełączeniu gałęzi” | Czy zmiany były zapisane commitem na poprzedniej gałęzi? | Kolejne przełączanie bez sprawdzenia stanu |
| „Merge nie daje tego, czego oczekiwałem” | Na której gałęzi byłeś w momencie scalania? | Powtarzanie scalania bez weryfikacji |
| „Usunąłem nie to” | Czy przed usunięciem wyszedłeś z katalogu i sprawdziłeś nazwę? | Dalsze kasowanie |

W każdej sytuacji awaryjnej kolejność jest stała:

```text
orientacja → stan → jedna decyzja → jedno działanie → ponowny stan
```

---

## Checklista cyklu życia (do odhaczania)

Odhaczaj dopiero, gdy potrafisz **powiedzieć, po co** jest dany etap:

- [ ] Mam katalog projektu  
- [ ] Mam lokalne repozytorium (historia może się zacząć)  
- [ ] Potrafię odróżnić katalog roboczy od obszaru przygotowania  
- [ ] Potrafię utworzyć commit jako decyzję, nie jako odruch  
- [ ] Potrafię odczytać historię  
- [ ] Potrafię utworzyć i wybrać gałąź  
- [ ] Wiem, że przed scaleniem wracam na gałąź docelową  
- [ ] Po scaleniu weryfikuję pliki i historię  
- [ ] Potrafię świadomie zakończyć lokalne repo usunięciem katalogu  

Jeśli któryś punkt jest tylko „kliknąłem / wpisałem”, wróć do teorii tego etapu.

---

## Czego ta pomoc celowo nie robi

- nie podaje gotowej sekwencji z karty ćwiczeń,
- nie podaje gotowych treści commitów z lekcji,
- nie rozwiązuje zadania za Ciebie,
- nie zastępuje sprawdzenia stanu.

Jej sukces wygląda tak:  
**Sam decydujesz, co jest potrzebne, i wiesz, której rodziny poleceń użyć.**
