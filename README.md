# JDSZR3-Git - część 1

## Historia

## Konfiguracja środowiska (dla tych, którzy nie zrobili tego w prework)
1. git config --global user.name "First name and lastname"
1. git config --global user.email "example@example.com"
1. git config --global credential.helper "cache --timeout=3600"
1. git config --global core.editor "code --wait"

### Zadanie 1.0
Ustaw powyższe wartości domyślne, jeżeli nie zrobiłeś tego podczas prework. Nie jesteś pewien? Sprawdź za pomocą `git config --list`

## Podstawowe komendy

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

### podstawowe komendy - wymiana danymi ze zdalnym repo (robimy często)
- `git push` - "wrzuca / wypycha" nasze na repo zdalne
- `git pull` - "zaciąga / pobiera" zmiany ze zdalnego repo i aktualizuje bieżący branch / HEAD
- `git fetch` - "zaciąga / pobiera" zmiany ze zdalnego repo bez  aktualizacji bieżącego branch / HEAD
- `git push origin --set-upstream feature/my-branch`, lub `git push origin -u feature/my-branch`, lub `git push origin -u HEAD` (jeżeli HEAD = feature/my-branch)

### zadanie 3.1
Pobierz zdalne repozytorium z GitHub, używając polecenia Git clone.


