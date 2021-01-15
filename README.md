# Git - ćwiczenie grupowe
# Przedstaw się!
Celem ćwiczenia jest zbudowanie całą drużyną pliku .xml który zawiera podstawowe informacje o was.

## Plik

Każda drużyna tworzy jeden plik - odpowiednio `<nazwa-teamu>.xml`.

Przykładowo: team o nazwie `SzybkieBizony` tworzy plik o nazwie `szybkie-bizony.xml`. 


### Plik jest w formacie:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<team name="{your team name}">
    <version>{your file version}</version>
    <members>
        <member name="{your name}" surname="{your surname}">{how to call you}</member>
    </members>
</team>
```

### Przykładowe uzupełnienie pliku:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<team name="ISA-MM-1">
    <version>3</version>
    <members>
        <member name="Michał" surname="Michalczuk">Michał</member>
        <member name="Agata" surname="Agatowska">Aga</member>
        <member name="Maciej" surname="Kowalski">Macias</member>
    </members>
</team>

```

## Zadanie
Waszym zadaniem jest uzupełnić ten plik. Ale jest parę reguł:
* każdy może dodać tylko swoje dane - tj autor commita musi się pokrywać z dodaną osobą
* każda zmiana składu musi być w oddzielnym commicie
* jeśli plik się zmienia (poprzez commit) należy podnieść wersję pliku o 1 - na początku jest 1
* gotowy plik można wrzucić do brancha `master` tylko przez `Pull Request` na GitHub'ie !
* branch zespołu powinien się nazywać `hello-nazwa-zespolu`

### Ćwiczenie A)
Wybierzcie czy chcecie pracować na jednym branchu, czy założyć wiele (per user) i wpiszcie członków drużyny wg powyższych reguł.

Które rozwiązanie jest dla was lepsze? Jakie problemy napotkaliście?

### Ćwiczenie B)
Wystawcie **jednego** `Pull Requesta` do repozytorium, do brancha master z danymi waszej drużyny.

Pull requesty sprawdzimy wspólnie na koniec i je zmergujemy.