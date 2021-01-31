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

### branches - podstawowe komendy
- `git branch` - sprawdź lokalne branche oraz aktywny branch
- `git branch -A ` - sprawdź wszystkie branche, w tym zdalne (będzie bardziej potrzebne w dniu 2.)
- `git branch my-new-branch` - tworzy branch o nazwie `my-new-branch`, z taką samą historią, jak obecny HEAD
- `git checkout my-other-branch` - przełącza HEAD na ostatni kommit brancha `my-other-branch`
- `git checkout -b my-third-branch` - połączenie dwóch powyższych. Tworzy nowy branch oraz "przechodzi na niego" (zmienia HEAD)

### zadanie 1.2
Stwórz nowy branch o nazwie `feature/moje-nazwisko-chapter-2` i dodaj tam kommit. W wyniku zadania na tym branchu powinno być o 1+ kommit więcej, niż na `master`
