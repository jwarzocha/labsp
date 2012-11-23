#Laboratorium 1
1. Używając linii poleceń stwórz strukturę katalogów:

temp
|-- dom
|-- nauka
|   |-- c
|   |-- logo
|   `-- pascal
`-- praca
    |-- dokumenty
    `-- zlecenia
        |-- niezrealizowane
        `-- zrealizowane
```sh
mkdir -p temp/dom
     mkdir -p temp/nauka/{c,logo,pascal}
     mkdir -p temp/praca/{dokumenty,zlecenia}
     mkdir -p temp/praca/zlecenia/{niezrealizowane,zrealizowane}
     cd temp | tree
```
        

2. Przejdź do katalogu dom i utwórz katalog wazne-sprawy.

3. Wejdź do katalogu wazne-sprawy i utwórz tam pusty plik rachunki.txt.

4. Będąc w katalogu wazne-sprawy skopiuj plik rachunki.txt do katalogu zrealizowane.

5. Przejdź do katalogu zrealizowane i zmień nazwę pliku rachunki.txt na wykonano.txt.

Polecenia: split, cat, diff

6. Utwórz plik wykonano.txt wielkości 11 bajtów, następnie podziel go pliki wielkości 5 bajtów. W ten sposób otrzymasz 3 pliki. (split)

7. Będąc w katalogu logo skopiuj powyżej otrzymane 3 pliki do katalogu dokumenty.

8. Będąc w katalogu dokumenty połącz skopiowane 3 pliki w plik odtworzono.txt, tak aby otrzymać plik o zawartości identycznej z wykonano.txt. Następnie plik odtworzono.txt skopiuj do katalogu wazne-sprawy.

9. Będąc w katalogu wazne-sprawy sprawdź, czy są jakieś różnice w zawartości plików wykonano.txt i odtworzono.txt.

10. Wyświetl kalendarz na październik 2009 r. (cal)

Wyświetl kalendarz na wrzesień, październik i listopad 2009 r. z miesiącami obok siebie (cal):

    wrzesień 2009       październik 2009        listopad 2009
ni po wt śr cz pi so  ni po wt śr cz pi so  ni po wt śr cz pi so
       1  2  3  4  5               1  2  3   1  2  3  4  5  6  7
 6  7  8  9 10 11 12   4  5  6  7  8  9 10   8  9 10 11 12 13 14
...                   ...                   ...

Wyświetl kalendarz na październik, listopad i grudzień 2009 r. w taki sposób:

     październik             listopad               grudzień
ni po wt śr cz pi so   ni po wt śr cz pi so   ni po wt śr cz pi so
             1  2  3    1  2  3  4  5  6  7          1  2  3  4  5
 4  5  6  7  8  9 10    8  9 10 11 12 13 14    6  7  8  9 10 11 12
11 12 13 14 15 16 17   15 16 17 18 19 20 21   13 14 15 16 17 18 19
...                    ...                    ...

I jeszcze raz na wrzesień i październik oraz na październik i listopad 2009 r z miesiącami obok siebie (cal, cut?):

     październik             listopad
ni po wt śr cz pi so   ni po wt śr cz pi so
             1  2  3    1  2  3  4  5  6  7
 4  5  6  7  8  9 10    8  9 10 11 12 13 14
11 12 13 14 15 16 17   15 16 17 18 19 20 21
...                    ...

11. Jaki był dzień tygodnia 25 maja 1975 r. (cal i date)



#Laboratorium 2



1. Wyświetl na ekran 2 pierwsze wiersze pliku program.c. (head)

2. Wyświetl na ekran 4 ostatnie wiersze pliku program.c. (head, tail)

3. W pliku program.c znajdź wszystkie wiersze z wystąpieniem słowa „main”. (grep)

4. Plikowi program.c nadaj następujące uprawnienia: właściciel – czytanie, pisanie, grupa – czytanie, pozostali użytkownicy: brak uprawnień. (chmod)

5. Będąc w katalogu temp przenieś katalog wazne-sprawy do katalogu praca.

6. Zarchiwizuj cały katalog temp. (zip i tar)

7. Usuń katalog temp.

8. Odtwórz z archiwum katalog temp. (unzip i tar)



#Laboratorium 3


1. Wyświetl plik /etc/passwd z podziałem na strony przyjmując, że strona na 5 linii tekstu. (raczej more niż less)

2. Korzystając z polecenia cat utwórz plik tekst3.txt, który będzie składał się z zawartości pliku tekst1.txt, ciągu znaków podanego ze standardowego wejścia (klawiatury) i pliku tekst2.txt.

3. Wyświetl po 5 pierwszych linii wszystkich plików w swoim katalogu domowym w taki sposób, aby nie były wyświetlane ich nazwy.

4. Wyświetl linie o numerach 3, 4 i 5 z pliku /etc/passwd.

5. Wyświetl linie o numerach 7, 6 i 5 od końca pliku /etc/passwd.

6. Wyświetl zawartość pliku /etc/passwd w jednej linii.

7. Za pomocą filtru tr wykonaj modyfikację pliku plik.txt, polegającą na umieszczeniu każdego słowa w osobnej linii.

8. Zlicz wszystkie pliki znajdujące się w katalogu /etc i jego podkatalogach.

9. Napisać polecenie zliczające ilość znaków z pierwszych trzech linii pliku /etc/passwd.
find /etc |head -3 |wc| tr '''\n'| tail -1



#Laboratorium 4



#Laboratorium 5
#Laboratorium 6 
#Laboratorium 7