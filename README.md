# JDSZR3-Git - część 1

## Historia

## Konfiguracja środowiska (dla tych, którzy nie zrobili tego w prework)
1. git config --global user.name "First name and lastname"
1. git config --global user.email "example@example.com"
1. git config --global credential.helper "cache --timeout=3600"
1. git config --global core.editor "code --wait"

### Zadanie 1.0
Ustaw powyższe wartości domyślne, jeżeli nie zrobiłeś tego podczas prework. Nie jesteś pewien? Sprawdź za pomocą `git config --list`

## I. Podstawowe komendy

### Zakładanie repozytorium (robimy 1 raz per repo)
- `git init` - tworzy puste nowe repozytorium w working directory. (sprawdzić go możemy poleceniem `pwd` - present working directory)

### Sprawdzanie "na czym stoimy" (robimy często)
- `git status` - sprawdza "na czym stoimy" - pokazuje oraz zmienione pliki oraz czy są one dodane do staging area
- `git diff` - to samo co git status, ale pokazuje zmiany w zawartości plików
- `git log` - sprawdzenie listy kommitów
- `git log --oneline` - sprawdzenie kommitów w krótszy, bardziej przejrzysty sposób

### Tworzenie kommitów
- `git add myfile.txt` - dodaje plik `myfile.txt` do staging area
- `git add .` / `git add -A` - dodaje wszystkie zmiany do staging area (robi je zielonymi)
- `git commit -m "Add users page to website"` - tworzy kommit z wiadomością `Add users page to website`. Ważne jest, aby w treści kommita pisać *sensowne rzeczy*, które opisują co zrobiliśmy. Najlepiej - pisać, PO CO są te zmiany lub "CO robią", gorzej - JAKIE są to zmiany, najgorzej - kommit nic nie wnoszący (some changes / minor bugfix / new improvements)

### Zadanie 1.1
*WAŻNE:*
W nazwach plików, folderów oraz później gałęzi (branches) warto unikać spacji oraz znaków innych niż te z alfabetu łacińskiego. Są na to 2 powody:
- znacznie ułatwia to życie podczas pracy w terminalu
- "tak się w programowaniu robi" (konwencja)

Przykład:
- zamiast "mój nowy plik.txt" -> my-new-file.txt (brak spacji i polskich znaków)
- zamiast "MyNewFile.txt" -> my-new-file.txt (zamiast dużych liter - same małe i myślniki jako spacje)

#### Przebieg zadania
- Stwórz (init) lokalne repozytoium *(pamiętaj o założeniu nowego katalogu i "przejściu" (polecenie `cd nazwa-katalogu`) do niego!)*
- sprawdź `git status`
- stwórz plik `hello-world.txt` z tekstem `Witaj świecie!`
- sprawdź `git status` i `git diff`
zakommituj go (pamiętaj o `git add` *PRZED commitem*)
- sprawdź `git status` i `git diff`
- sprawdź `git log` lub `git log --oneline`

#### Wizualizacja procesu komitowania i `areas` w Git:
![git 3 areas example](https://snipcademy.com/img/articles/git-fundamentals/three-stages-01.svg)

### II. Branches

#### Czym są i po co są potrzebne branche.

#### Branches - podstawowe komendy

- `git branch` - sprawdź lokalne branche oraz aktywny branch
- `git branch -A ` - sprawdź wszystkie branche, w tym zdalne (będzie bardziej potrzebne w dniu 2.)
- `git branch my-new-branch` - tworzy branch o nazwie `my-new-branch`, z taką samą historią, jak obecny HEAD
- `git checkout my-other-branch` - przełącza HEAD na ostatni kommit brancha `my-other-branch`
- `git checkout -b my-third-branch` - połączenie dwóch powyższych komend. Tworzy nowy branch oraz "przechodzi na niego" (zmienia HEAD)

### Zadanie 2.1
- Stwórz plik book.txt, wprowadź w nim jakiś tekst, może być 1. rozdział książki o Git, zakommituj plik (`git add .`, potem `git commit`)
- Stwórz nowy branch o nazwie `feature/nazwisko-chapter-2` (`git checkout -b feature/nazwisko-chapter-2`) i dodaj tam kommit.

W wyniku zadania na tym branchu powinno być o 1+ kommit więcej, niż na `master`.
Upewnić się możesz za pomocą `git log --oneline`.
Po zrobieniu kommit użyj polecenia `git checkout master` (zauważ brak modyfikatora `-b`, który tworzy nowy branch) i zobacz, że plik wrócił do poprzedniej wersji. Spróbuj przełączyć się pomiędzy branch'ami kilka razy.

#### Detached HEAD

Występuje wtedy, kiedy HEAD nie wskazuje na branch, a wskazuje na kommit.
Wtedy, podczas tworzenia nowego commita, na niego nie będzie wskazywać żadny branch.
Z tym wiąże się ryzyko, że jeżeli przepniemy HEAD na inny branch/kommit, nasz nowy kommit, zrobiony w trybie detached HEAD będzie stracony.

- `git checkout ab123xyz` - przechodzi na kommit z ID, zaczynającym się od `ab123xyz`
- Przypominajka: `git checkout -b feature/some-fix` - tworzy nowy branch i "przepina" na niego HEAD. Jest to najprostszy sposób zabezpieczyć swoją pracę.


## III. Podstawy pracy ze zdalnym repozytorium

- Git != GitHub
- można pracować na zdalnym repo w pojedynkę
- GitHub służy do wymiany danymi, ale nie jest on "lepszy" od zwykłego członka zespołu - jest takim samym 

### podstawowe komendy - pobieranie / wiązanie repozytorium (robimy 1 raz per repo)

**Ważne**: z dwóch poniższych poleceń robimy zwykle jedno - albo git init, albo git clone.

Init + remote add origin - kiedy tworzymy nowe repo lokalnie (rzadko)

Clone - kiedy chcemy, aby na naszym lokalnym urządzeniu pojawiło się już istniejące, wcześniej stworzone repo.

- `git clone git@github.com:mojaorganizacja/mojerepo.git` - tworzy katalog o nazwie `mojerepo` i kopiuje tam zdalne repozytorium. Robimy **ZAMIAST** `git init`. Istotna różnica - na odmianę od `git init` tworzy nowy katalog, zamiast tworzyć repo w bieżącym.
- `git remote add origin git@github.com:mojaorganizacja/mojerepo.git` - "wiąże lokalne i zdalne repozytorium". Robimy **PO WCZEŚNIEJSZYM** `git init`. Używane raczej rzadko.

### zadanie 3.1 - klonowanie zdalnego repo
Pobierz zdalne repozytorium z GitHub, używając polecenia Git clone.

### podstawowe komendy - wymiana danymi ze zdalnym repo (robimy często)
- `git push` - "wrzuca / wypycha" nasze na repo zdalne
- `git pull` - "zaciąga / pobiera" zmiany ze zdalnego repo i aktualizuje bieżący branch / HEAD
- `git fetch` - "zaciąga / pobiera" zmiany ze zdalnego repo bez  aktualizacji bieżącego branch / HEAD
- `git push origin --set-upstream feature/my-branch`, lub `git push origin -u feature/my-branch`, lub `git push origin -u HEAD` (jeżeli HEAD = feature/my-branch)

### Zadanie 3.2 - pobieranie zmian od trenera
- Na gałęzi `master` dokonaj jakichś zmian w pliku `book.txt`.
- Spróbuj pobrać zmiany od trenera ze zdalnego repo (`git pull`)
- Zobacz, że jest błąd, ponieważ zmiany kolidują
- Odrzuć lokalne zmiany (`git reset --hard`). **Uwaga** - to polecenie usuwa zmiany bez możliwości powrotu. Jeżeli chcesz je zachować - zrób nowy branch i stwórz na nim kommit.
- Ponownie zrób `git pull`

### Zadanie 3.3 - "wypchnięcie lokalnego branch"
- Zrób branch `feature/zadanie-3.3-nazwisko`
- Zrób na tym branch nowy plik o nazwie `zadanie-3.3-nazwisko.txt`
- Zrób `git push`, zaobserwuj błąd
- Zrób `git push origin -u feature/zadanie-3.3-nazwisko` (pilnuj poprawności nazwy branch), lub `git push origin -u HEAD` (pro-tip, żeby mniej wpisywać :) )
- Zaobserwuj, że na GitHub pojawił się nowy branch

## IV. Przywracanie zmian w GIT
- Bardzo przydatna funkcjonalność GITa przy pracy zespołowej

### Podstawowe komendy:
`git checkout` - zamienia wskaźnik HEAD na wskazany commit lub branch. 

`git revert` - odwraca zmiany do wybranego momentu i zapisuje je jako nowy commit

`git reset` - przywraca zmiany w repo do wybranego momentu z historią włącznie.

**Po zadaniach wyciągniemy wnioski!** 

### Zadanie 4.1.
- Na branchu `master` dokonajmy zmian w jednym z istniejących plików. Zapisz zmiany
- Następnie zapiszmy zmiany za pomocą `git commit -m "Added changes in twojanazwapliku.txt for ex 4.1"
- Wykonaj ponownie powyższe dwa kroki
- Przejdziemy teraz do procesu przywracania pliku do stanu sprzed pierwszą edycją. Użyj: `git log --oneline`
- Po znalezieniu odpowiedniego hashu commita wykonajmy `git checkout [hashId]` 
- Sprawdź jakie zmiany zostały dokonane `git status`.
- Wróćmy do stanu początkowego `git checkout master`. Przeniesie nas on do wersji po wykonaniu zmian.

### Zadanie 4.2
- Na branchu `master` dokonajmy zmian w jednym z istniejących plików. Zapisz zmiany
- Następnie zapiszmy zmiany za pomocą `git commit -m "Added changes in twojanazwapliku.txt for ex 4.2"
- Przejdziemy teraz do procesu przywracania pliku do stanu sprzed pierwszą edycją. Użyj: `git log --oneline`
- Po znaleznieniu odpowiedniego hashu commita wykonajmy `git revert [hashId]`
- Zostanie stworzony nowy commit. Należy nadać mu tytuł i komentarz.
- Sprawdźmy stan naszego repozytorium za pomocą `git log --oneline`.
- Sprawdźmy zawartość naszego repozytorium i wyciągnijmy wnioski.

### Zadanie 4.3
- Na branchu `master` dokonajmy zmian w jednym z istniejących plików. Zapisz zmiany
- Następnie zapiszmy zmiany za pomocą `git commit -m "Added changes in twojanazwapliku.txt for ex 4.2"
- Przejdziemy teraz do procesu resetowania repozytorium do stanu sprzed edycją. Użyj `git log --oneline`
- Po znalezieniu odpowiedniego hashu commita wykonajmy `git reset --hard [hashId]`
- Sprawdźmy stan naszego repozytorium za pomocą `git status` a następnie `git log --oneline`.
- Sprawdźmy zawartość naszego repozytorium i wyciągnijmy wnioski.

## Zadanie 4.4 (dla chętnych)
- Wykonaj zadanie 4.3 dodając do komendy `git reset` parametry `--soft` oraz `--mixed` zamiast `--hard`. Sprawdź jak zachował się git.

## V. Scalanie branchy

### Podastawowe komendy:

`git merge [branch-name]` - dołącza do aktualnego brancha branch, który podamy w parametrze
`git rebase [branch-name]` - wykonuje operację rebase 

**Działanie**
`git merge` - git tworzy nowy commit, który zawiera nasze zmiany i zmiany z innego brancha.
`git rebase` - git zmienia nam podstawowy commit, z którego wychodzi nasz obecny branch

**UWAGA**
- podczas wykonywania operacji merge mogą pojawić się `konflikty`. Występują one, gdy w obu wersjach branchy nastąpiły zmiany w tym samym pliku.

## Zadanie 5.1 
- Stwórzmy nowy branch `git branch feature/merge`
- Stwórzmy nowy plik `fileA.txt`. Dodaj losowy tekst do pliku.
- Przełączmy się do brancha master `git checkout master`
- Wykonajmy operację merge z wcześniej dodanym branchem `git merge feature/merge`
- Zaobserwujmy co się stało.

## Zadanie 5.2
- Upewnij się że jesteś na branchu master
- Utwórz branch `feature/rebase`
- Utwórz plik `plikA.txt` i wykonaj operację commit z wiadomością `Added plikA` oraz plik B i wykonaj operację commit z wiadomością `Added plikB`
- Przełącz się na branch master
- Utwórz plik `plikC.txt` i wykonaj operację commit z wiadomością `Added plikC`.
- Przełącz się na branch feature/rebase.
- Przeprowadź operację rebase do mastera `git rebase master`

## Zadanie 5.3
- Stwórzmy nowy branch `git branch feature/conflicts`
- Stwórzmy nowy plik `conflictedFile.txt` i wpiszmy tekst `Nie ma konfliktów`. Wykonajmy operację commit.
- Stwórzmy nowy branch `git branch feature/conflicts2`
- Dokonajmy zmiany w pliku `conflictedFile.txt` - wpiszmy tekst `Będą konflikty`. Wykonajmy operację commit
- Przełąz się na branch `feature/conflicts` i wykonaj operację `merge` z brancha `feature/conflicts2`.

## VI. Dobre praktyki przy opisywaniu zmian.
- Dzielimy komentarz na tytuł oraz treść
- Krótki i zwięzły tytuł
- Zdania zaczynamy wielką literą
- Tytuł - zdania w trybie rozkazującym
- Komentarz powinien być lakoniczny i opisywać gdzie wykonano zmiany i dlaczego.

### Zadanie 6.1
- Wejdź do swojego repozytorium.
- Dodaj plik `firstFile.txt`. Napisz dwa zdania i zapisz go.
- Zrób `git add .` następnie `git commit` 
- Po wykonaniu komendy `git commit` powinien otworzyć się nam wybrany w zadaniu nr 6 edytor tekstowy.
- Stwórz wiadomość w następujący sposób: w pierwszej linijce umieść tytuł, zrób jedną linię przerwy, umieść komentarz. Wykonaj wszystko według zasad. Kliknij enter.
- Po co to wszystko? Wykonaj `git log` a następnie `git log --oneline`

https://chris.beams.io/posts/git-commit/

## VII. Pull request
### Idea pull requestów:
- Wąskie grono osób z uprawnieniami zapisu
- Kontrola nad wchodzącymi zmianami
- Przeglądanie i ocena kodu
- Testowanie automatyczne

### Flow:
- Kopia repozytorium znajduje się na koncie użytkownika
- Dowolnie możemy manewrować zmianami
- Przygotowujemy zmianę i pushujemy do Githuba.
- Pull request trafia do autora projektu źródłowego
- Od polityki autora zależy dalszy los wprowadzonej zmiany
- Github pozwala prowadzić dyskusję nad Pull Requestem.

### Zadanie 7.1 Tworzymy pierwszy pull request:

## VIII. Q&A - Praktyka pracy z GITem

**Istnieją różne GUI do zarządzania Gitem:**
- TortoiseGit
- GitKraken
- Github GUI
- Bitbucket GUI

**Nie tylko github!**
- Gitlab
- Bitbucket
- A może własne repozytorium git na swoim domowym serwerze?

### Pytania od kursantów? :)

