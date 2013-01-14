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


1. Wyświetl listę plików z aktualnego katalogu, zamieniając wszystkie małe litery na duże.
```sh
    ls | tr [:lower:] [:upper:] (nie obsługuje znaków narodowych)
```
```sh
    ls | tr a-z A-Z
```
```sh
    ls | tr [:lower:]ąęćłśżź [:upper:]ĄĘŁŚŻŹ
```

2. Wyświetl listę praw dostępu do plików w aktualnym katalogu, ich rozmiar i nazwę.
```sh
    ls -l | awk '{print $1,$5,$9}'
```
```sh
    find . -type f -exec ls -l '{}' ';' | cut -d ' ' -f1,5,9 (nie działa dla plików z datami dwucyfrowymi)
```
```sh
    ls --format=long --human-readable
```
```sh
    find . -printf "Plik: %f Rozmiar: %s Prawa: %M \n" -maxdepth 1
```

3. Wyświetl listę plików w aktualnym katalogu, posortowaną według rozmiaru pliku.
```sh
    ls -l | sort -k5,5
```
```sh
    ls -lrS
```
```sh
    find . -maxdepth 1 -not - type d -exec ls -l '{}' ';' | sort -n -t ' ' -k6,6
```
```sh
    ls --sort=size -1
```

4. Wyświetl zawartość pliku /etc/passwd posortowaną według numerów UID w kolejności od największego do najmniejszego.
```sh
    cat /etc/passwd | sort -n -t ':' -k3,3
```
```sh
    sort -t : -n -k3 -r /etc/passwd
```
```sh
    cat /etc/passwd | sort -r -t: -g -k 3
```
```sh
    sort -t : -k3 -nr /etc/passwd
```
```sh
    cat /etc/passwd/ | sort --reverse --general-numeric-sort
```
5. Wyświetl zawartość pliku /etc/passwd posortowaną najpierw według numerów GID w kolejności od największego do najmniejszego, a następnie UID.
```sh
    sort -t : -k4 -r /etc/passwd | sort -t : -k3
```
```sh
    cat /etc/passwd | sort --field-separator=":"
```
```sh
    cat /etc/passwd | sort -r --field-separator=":" -g -k 4,3
```

6. Podaj liczbę plików każdego użytkownika.
```sh
    find $HOME -not -type d | wc -l
```
```sh
    find / -printf "%u\n" 2> /dev/null | sort | uniq -c
```

7. Sporządź statystykę praw dostępu (dla każdego z praw dostępu podaj ile razy zostało ono przydzielone).
```sh
    find -printf "%m\n" | sort | uniq -c
```

8. Czy potrafisz odpowiedzieć jaki będzie efekt wykonania poniższych poleceń?

ls -l > lsout.txt                           #  1
```sh
    Utwotrzenie pliku lsout.txt i wypelnienie jej lista plikow w akutalnym katalogu
```
ls -la >> lsout.txt                         #  2
```sh
    Dopisuje do pliku lsout.txt liste uruchomionych procesów
```
ps >> psout.txt                             #  3
```sh
    Dopisuje ilosc wolnej pamięci
```
 
 

#Laboratorium 5



1. Znajdź w swoim katalogu domowym (bez podkatalogów) wszystkie pliki, które zostały zmodyfikowane w ciągu ostatnich dziesięciu dni i wyświetl ich nazwy.
```sh
    find ~/ -maxdepth 1 -mtime -10 -type f (maxdepth podać pierwsze w kolejności)
```

2. Znajdź wszystkie pliki zwykłe w systemie, które mają w nazwie ciąg znaków „conf” i wyświetl ich nazwy na ekranie.
```sh
    find  /etc -name \*config\* -type f 2> /dev/null
```

3. Znajdź w swoim katalogu domowym wszystkie pliki, które nie były używane w ciągu ostatnich 20 dni.
```sh
    find ~/ \( -type d -name ".git" -prune \) -o \( -type f -print \)
```
```sh
    find ~/ -atime 20 (nie do końca)
```
```sh
    find . -path '*/.git/*' - prune -o -print
```
```sh
    -mtime -20 | egrep -v '/\.git' (praktyczniejsza wersja z mtime)
```
```sh
    find . ! -regex ".*/\.git/?.*"
```
4. Znajdź w katalogu /etc wszystkie niepuste podkatalogi i pliki o nazwach zaczynających się na literę „a”.
```sh
    find /etc \( -type f -and -name a* \) -or \( -type d -and ! -empty \) 2> /dev/null
```
```sh
    find /etc\(-type d -and ! empty\) -or \(-type f -and -name a*\) 2> /dev/null
```
Zadania różne

5. Z bieżącego katalogu usuń pliki, których nazwa zaczyna się na literę „x” i zawiera dokładnie trzy znaki.
```sh
    rm x??
```
6. Skonstruuj polecenie tworzące katalog, którego nazwą będzie aktualna (w momencie wywołania) systemowa data w formacie rrrr-mm-dd.
```sh
    mkdir date +%Y-%m-%d
```



#Laboratorium 6



1. W pliku plik.txt znajdź wiersze zawierające co najmniej jeden znak.
```sh
    grep . {1,} plik.txt
```

2. Znajdź w plikach pl* wiersze rozpoczynające się od cyfry.
```sh
    grep ^[0-9] pl*
```

3. Znajdź pliki, zawierające wiersz w którym na 9 pozycji występuje litera r.
```sh
    ls -1 | grep -E '^.{8}r.*'
```

4. Policz, ilu użytkowników systemu używa powłoki bash (zgodnie z zapisami w pliku /etc/passwd).
```sh
    grep -c bash /etc/passwd
```

5. Znajdź wiersze zawierające liczby rzymskie w pliku plik.txt.
```sh
    egrep "(X|D|C|M|V|L|I){1,}" plik.txt
```



#Laboratorium 7



1. W bieżącym katalogu zamienić rozszerzenia wszystkich plików z rozszerzeniem htm na html. Jeżeli w nazwie pliku istnieje spacja, to należy zamienić ją na znak podkreślenia.
```sh
    #!/bin/bash

     for plik1 in *.htm
     do
       plik2=`echo "$plik1"l | tr " " "_"`
       mv "$plik1"  "$plik2"

     done
     exit 0
```

2. Napisać skrypt zawierający funkcję obliczającą silnię. Następnie należy obliczyć silnię z liczby, która jest argumentem skryptu. W przypadku niepoprawnego argumentu należy wypisać odpowiedni komunikat.
```sh
    #!/bin/bash
     if [ $# -eq 0 ]
     then
       echo "Wpisz: bash $0 liczba_naturalna"
       exit 1
     fi
     silnia=1
     for (( i=1; i<=$1; i++ ))
     do
       silnia=`expr $silnia \* $i`
     done
     echo "Silnia z liczby $1 = $silnia"
     exit 0
```

3. Napisać skrypt zbierający jak najwięcej informacji o użytkowniku, którego login jest argumentem skryptu. Jeżeli skrypt nie ma argumentu, to należy użyć login osoby uruchamiającej skrypt.
```sh
    if [ $# -ge 1 ];
     then
         user=$1
     else
         user=`whoami`
     fi
     id $user 2> /dev/null > /dev/null
     if [ $? -eq 0 ];
     then
         echo "Uzytkownik nazywa sie $user"
         users | grep -w "$user" > /dev/null 2> /dev/null
         if [ $? -eq 0 ];
         then
         echo "Jest aktualnie zalogowany"
         else
         echo "Nie jest aktualnie zalogowany"
         fi
         echo "Nalezy do grup: "`id $user -gn`
         user_passwd=`cat /etc/passwd | grep -w $user`
         if [ $? -eq 0 ];
         then
         home_dir=`echo $user_passwd | cut -d ":" -f 6`
         shell=`echo $user_passwd | cut -d ":" -f 7`
         echo "Katalog domowy to $home_dir a powloka jakiej uzywa to $shell"
         else
         echo "W pliku /etc/passwd nie ma informacji o tym uzytkowniku"
         fi
     else
         echo "Uzytkownik $user nie istnieje"
     fi
```

4. Napisz skrypt usuwający z katalogu domowego i jego podkatalogów wszystkie pliki zwykłe o nazwie 'core' starsze niż 3 dni.
```sh
    #!/bin/bash

     elif=`find ~ -name "core" -ctime +3  -type f`
     rm "$elif"
     echo "Zrobione"
     exit 0
```


#skrypty

1.skrypt wyliczający n-ty wyraz ciagu fibonacciego
```sh
#!/bin/bash
 if [ $# -eq 0 ]
 then
   echo "Wpisz: bash $0 liczba_naturalna"
   exit 1
 fi
 x=0 # <=teraz jest to zerowy wyraz ciagu fib
 y=1 # <=teraz jest to pierwszy wyraz ciagu fib
 for (( i=2; i<=$1; i++ ))# zaczynamy od 2 bo obliczamy anjpierw drugi wyraz c.f.
 # pętla bedzie działac az dojdzie do podanej liczby naturalnej 
 do
   a=$[x+y] #dodajemy dwa poprzednie wyrazy c.f.
    		#z ich dodanie powstaje a
   x=$y # tearz pierwszym poprzednim wyrazem jest y
   y=$a # a drugim jest a aleprzy wyjsciu z petli a jest n-tym
		#wyrazem ciagu fib
 done
 echo " $1 wyraz ciągu Fibonaciego = $a"
 exit 0
 ```
 2.skrypt liczacy ile lini napisałes we wszystkich programach c i c++
 ```sh
 #!/bin/bash
szukaj=(`find -type f \( -name "*.c" -o -name "*.cpp" \)`) #-type f powoduje wyswietlenie tylko plikow
#wyszukuje ^pliki c i c++
#liczy liczbe wszystkich plikow v
echo "Liczba plikow: ${#szukaj[*]}"
a=0 # poczatkowa wartosc liczby linijek
for(( i=0; i<${#szukaj[*]}; i++ ))
do 
  LINES=`wc -l < ${szukaj[i]}` #liczba linijek w pliku numer i
  echo "Plik ${szukaj[i]} $LINES" #wypisuje liczbe linijek w i tym pliku
  a=$[LINES+a] #sumuje linijki
done
echo "Napisałes juz $a linijek" #wypisuje sume linijek
exit 0
```

robi to samo co wyzej
```sh
#!/bin/bash
  find -type f \( -name "*.c" -o -name "*.cpp" \) -print0 | wc -l --files0-from=- 
 exit 0
```
```sh
#!/bin/bash
	
	echo "$#"
	
	case $# in
		"1") szukaj=(`find $1 -type f \( -name "*.c" -o -name "*.cpp" \)`);; #-type f powoduje wyswietlenie tylko plikowszukaj=(`find  -type f \( -name "*.c" -o -name "*.cpp" \)`) #-type f powoduje wyswietlenie tylko plikow
		"2") szukaj=(`find $2 -type f \( -name "*.c" -o -name "*.cpp" \)`);; #-type f powoduje wyswietlenie tylko plikow
		"3") szukaj=(`find $3 -type f \( -name "*.c" -o -name "*.cpp" \)`);; #-type f powoduje wyswietlenie tylko plikow
	esac
	
	#wyszukuje ^pliki c i c++
	#liczy liczbe wszystkich plikow v
	echo "Liczba plikow: ${#szukaj[*]}"
	a=0 # poczatkowa wartosc liczby linijek
	for(( i=0; i<${#szukaj[*]}; i++ ))
	do 
		if [[ $1 == "-c" ]] ; then
			LINES=`cat ${szukaj[i]} | grep -v "^$" | grep -v "//" | wc -l ` #liczba linijek w pliku numer i
		else
			LINES=`wc -l < ${szukaj[i]}` #liczba linijek w pliku numer i
		fi
		echo "Plik ${szukaj[i]} $LINES" #wypisuje liczbe linijek w i tym pliku
		a=$[LINES+a] #sumuje linijki
	done
	echo "Napisałes juz $a linijek" #wypisuje sume linijek
	exit 0

```
