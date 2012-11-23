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
```sh
     cd dom
     mkdir wazne-sprawy
```

3. Wejdź do katalogu wazne-sprawy i utwórz tam pusty plik rachunki.txt.
```sh
     cd wazne-sprawy
     touch rachunki.txt
```

4. Będąc w katalogu wazne-sprawy skopiuj plik rachunki.txt do katalogu zrealizowane.
```sh
    cp rachunki.txt ../../praca/zlecenia/zrealizowane/rachunki.txt
```

5. Przejdź do katalogu zrealizowane i zmień nazwę pliku rachunki.txt na wykonano.txt.
```sh
     cd ../..
     cd praca/zlecenia/zrealizowane
     mv rachunki.txt wykonano.txt
```

6. Utwórz plik wykonano.txt wielkości 11 bajtów, następnie podziel go pliki wielkości 5 bajtów. W ten sposób otrzymasz 3 pliki. (split)
```sh
    cat > wykonano.txt 
    12345678901 (potem wcisnąć Ctrl+D)
    split -b 5 wykonano.txt
```

7. Będąc w katalogu logo skopiuj powyżej otrzymane 3 pliki do katalogu dokumenty.
```sh
    cp ../../praca/zlecenia/zrealizowane/x* ../../praca/dokumenty
```

8. Będąc w katalogu dokumenty połącz skopiowane 3 pliki w plik odtworzono.txt, tak aby otrzymać plik o zawartości identycznej z wykonano.txt. Następnie plik odtworzono.txt skopiuj do katalogu wazne-sprawy.
```sh
     cat xaa xab xac > odtworzono.txt
     cp odtworzono.txt ../../dom/wazne-sprawy/odtworzono.txt
```

9. Będąc w katalogu wazne-sprawy sprawdź, czy są jakieś różnice w zawartości plików wykonano.txt i odtworzono.txt.
```sh
     diff -a ../../praca/zlecenia/zrealizowane/wykonano.txt odtworzono.txt
```

10. Wyświetl kalendarz na październik 2009 r. (cal)

Wyświetl kalendarz na wrzesień, październik i listopad 2009 r. z miesiącami obok siebie (cal):

```sh
    cal 10 2009
```

Wyświetl kalendarz na październik, listopad i grudzień 2009 r. w taki sposób:

```sh
    cal -3 2009
```

I jeszcze raz na wrzesień i październik oraz na październik i listopad 2009 r z miesiącami obok siebie (cal, cut?):

```sh
    cal 11 2009 -3m
```

11. Jaki był dzień tygodnia 25 maja 1975 r. (cal i date)

```sh
    date -d 1975-05-25 +%A
```



#Laboratorium 2



1. Wyświetl na ekran 2 pierwsze wiersze pliku program.c. (head)
```sh
    head -n 2 program.c
```

2. Wyświetl na ekran 4 ostatnie wiersze pliku program.c. (head, tail)
```sh
    tail -n 4 program.c
```

3. W pliku program.c znajdź wszystkie wiersze z wystąpieniem słowa „main”. (grep)
```sh
    grep "main" program.c
```

4. Plikowi program.c nadaj następujące uprawnienia: właściciel – czytanie, pisanie, grupa – czytanie, pozostali użytkownicy: brak uprawnień. (chmod)
```sh
    chmod 650 program.c
```
```sh
    chmod u+rw program.c
    chmod g+r program.c
    chmod o-rwx program.c
```

5. Będąc w katalogu temp przenieś katalog wazne-sprawy do katalogu praca.
```sh
    mv dom/wazne-sprawy praca/wazne-sprawy
```

6. Zarchiwizuj cały katalog temp. (zip i tar)
```sh
    tar -cvf temp.tar temp
    gzip temp.tar
```

7. Usuń katalog temp.
```sh
    zip -r temp.zip temp
```

8. Odtwórz z archiwum katalog temp. (unzip i tar)
```sh
    tar -zxf temp.tar.gz
     unzip temp.zip
```
9. Posprzątaj na swoim koncie.
```sh
     cd ~/tmp
     rm -rf *
```



#Laboratorium 3


1. Wyświetl plik /etc/passwd z podziałem na strony przyjmując, że strona na 5 linii tekstu. (raczej more niż less)
```sh
     more -5 /etc/passwd
```

2. Korzystając z polecenia cat utwórz plik tekst3.txt, który będzie składał się z zawartości pliku tekst1.txt, ciągu znaków podanego ze standardowego wejścia (klawiatury) i pliku tekst2.txt.
```sh
    cat tekst1.txt - tekst2.txt > tekst3.txt
```
```sh
    cat tekst1.txt > tekst3.txt
    cat >> tekst3.txt
    cat tekst2.txt >> tekst3.txt
```

3. Wyświetl po 5 pierwszych linii wszystkich plików w swoim katalogu domowym w taki sposób, aby nie były wyświetlane ich nazwy.
```sh
    head $HOME/* -n 5 -q
```
```sh
    head -qn 5 *
```

4. Wyświetl linie o numerach 3, 4 i 5 z pliku /etc/passwd.
```sh
    head -n 5 /etc/passwd | tail -n 3
```

5. Wyświetl linie o numerach 7, 6 i 5 od końca pliku /etc/passwd.
```sh
    tail -n 7 /etc/passwd | head -n 3
```

6. Wyświetl zawartość pliku /etc/passwd w jednej linii.
```sh
    cat /etc/passwd | tr "n" " "
```

7. Za pomocą filtru tr wykonaj modyfikację pliku plik.txt, polegającą na umieszczeniu każdego słowa w osobnej linii.
```sh
    cat plik.txt | tr " \t" "\n"
```

8. Zlicz wszystkie pliki znajdujące się w katalogu /etc i jego podkatalogach.
```sh
    find /etc -type f 2> dev/null/ wc -l
```
```sh
     find /etc -type f 2> errors | wc -l
```
```sh
    find /etc -type f -follow | wc -l
```
```sh
    head -n 0 /etc/* | tr -s '[n*2]' 'n' | wc -l
```


9. Napisać polecenie zliczające ilość znaków z pierwszych trzech linii pliku /etc/passwd.
```sh
     find /etc/ | head -3 | wc | tr '''\n' | tail -1
```
```sh
    find /etc/ | head -3 | wc -c
```
```sh
     cat /etc/passwd/ | head -n 3 | wc -m  

```
```sh
    head /etc/passwd -n 3 | wc -c
```
```sh
    cut /etc/passwd | head -n 3 | wc -n
```



#Laboratorium 4



#Laboratorium 5
#Laboratorium 6 
#Laboratorium 7