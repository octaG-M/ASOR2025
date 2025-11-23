# Istoria shell-urilor UNIX

Independența shell-ului față de sistemul de operare UNIX în sine a dus la dezvoltarea a zeci de shell-uri de-a lungul istoriei UNIX — deși doar câteva au ajuns să fie folosite pe scară largă.

## Bourne shell

Primul shell important a fost Bourne shell (numit după inventatorul său, Steven Bourne); acesta a fost inclus în prima versiune populară de UNIX, Version 7, începând cu anul 1979. Bourne shell este cunoscut în sistem sub numele sh. Deși UNIX a trecut prin foarte multe schimbări, Bourne shell este încă popular și practic neschimbat. Mai multe utilitare UNIX și funcții de administrare depind de el.
Primul shell alternativ utilizat pe scară largă a fost C shell, sau csh. Acesta a fost scris de Bill Joy la Universitatea din California, Berkeley, ca parte a distribuției Berkeley Software Distribution (BSD) a UNIX, care a apărut câțiva ani după Version 7.

## C shell

C shell și-a primit numele datorită asemănării comenzilor sale cu instrucțiunile din limbajul de programare C, ceea ce îl face mai ușor de învățat pentru programatorii de pe sistemele UNIX. Suportă mai multe funcții ale sistemului de operare (de ex., controlul job-urilor; vezi Capitolul 8) care erau unice pentru BSD UNIX, dar care între timp au migrat în majoritatea versiunilor moderne. De asemenea, are câteva funcții importante (de ex., alias-uri; vezi Capitolul 3) care îl fac în general mai ușor de folosit.

## Korn shell

În ultimii ani, mai multe alte shell-uri au devenit populare. Cel mai notabil dintre acestea este Korn shell. Acest shell este un produs comercial care încorporează cele mai bune funcții ale Bourne și C shell-urilor, plus multe caracteristici proprii. Korn shell este similar cu bash în majoritatea privințelor; ambele includ o mulțime de funcții care le fac ușor de utilizat. Avantajul lui bash este că este gratuit. Pentru informații suplimentare despre Korn shell, vezi Anexa A.


# Caracteristicile shell-ului bash
Deși shell-ul Bourne este încă considerat „shell-ul standard”, bash devine din ce în ce mai popular. Pe lângă compatibilitatea cu Bourne shell, bash include:
- cele mai bune caracteristici ale shell-ului C
- funcționalități din Korn shell
- câteva avantaje proprii

## Editarea liniei de comandă
Una dintre primele funcții care atrag utilizatorii către bash este editarea liniei de comandă. 
Aceasta îți permite:
- să revii și să corectezi greșeli mult mai ușor
- să modifici comenzi deja introduse

Este mult mai ușor de folosit decât mecanismul de istoric al C shell, iar Bourne shell nu oferă deloc această posibilitate.

## Controlul job-urilor (job control)
O altă caracteristică majoră a shell-ului bash, utilă în special pentru utilizatorii interactivi, este controlul job-urilor. Această funcționalitate permite:
- oprirea unor comenzi
- pornirea lor
- întreruperea temporară (pauză) a oricărui număr de procese

Această caracteristică a fost preluată aproape identic din C shell. 

## Avantaje pentru personalizare și programare

Restul avantajelor bash sunt orientate către utilizatorii care:
- personalizează comportamentul shell-ului
- scriu scripturi sau programe complexe

Printre funcționalități se numără:
- numeroase opțiuni și variabile pentru configurare
- definirea de funcții
- structuri de control extinse
- aritmetică pe numere întregi
- control avansat al I/O
- multe alte extinderi utile pentru programatori


# Folosirea bash

Este posibil să folosiți sau nu bash în acest moment. Administratorul de sistem probabil a configurat contul dvs. cu shell-ul pe care îl folosește el ca „standard” pe sistem. Este posibil să nu fiți nici măcar conștient că există mai multe shell-uri disponibile.

Totuși, este ușor să determinați ce shell folosiți. Conectați-vă la sistem și tastați la prompt:

```
echo $SHELL
```

Veți vedea un răspuns care conține sh, csh, ksh sau bash; acestea indică shell-urile Bourne, C, Korn și bash, respectiv. (Există și posibilitatea să folosiți un alt shell, cum ar fi tcsh.)

Dacă nu folosiți bash și doriți să-l folosiți, trebuie mai întâi să aflați dacă este instalat pe sistemul dvs. Pur și simplu tastați:
```
bash
```

Dacă primiți un prompt nou format dintr-o anumită informație urmată de un semn dolar, de exemplu:
```
bash3 $
```
atunci totul este în regulă. 

Tastați: 
```
exit
```
pentru a reveni la shell-ul normal.


Dacă primiți un mesaj de tip:
```
not found
```
este posibil ca sistemul dvs. să nu aibă bash instalat. Întrebați administratorul de sistem sau un alt utilizator cunoscător; există șansa să aveți o versiune de bash instalată într-un loc (director) care nu este accesibil în mod normal pentru dvs. Dacă nu, citiți Capitolul 11 pentru a afla cum puteți obține o versiune de bash.

Odată ce știți că aveți bash pe sistem, îl puteți porni din orice alt shell pe care îl folosiți, tastând: 
```
bash
```
așa cum s-a arătat mai sus. 

Totuși, este mult mai bine să-l instalați ca shell-ul de login, adică shell-ul pe care îl primiți automat ori de câte ori vă conectați. Este posibil să puteți face instalarea singur. Iată instrucțiuni concepute să funcționeze pe o varietate cât mai largă de sisteme UNIX. Dacă ceva nu funcționează (de exemplu, tastați o comandă și primiți un mesaj de eroare `not found` sau o linie goală ca răspuns), va trebui să întrerupeți procesul și să contactați administratorul de sistem. Alternativ, consultați Capitolul 12, unde se demonstrează o metodă mai puțin directă de a înlocui shell-ul curent.
Trebuie să aflați unde se află bash pe sistem, adică în ce director este instalat. Puteți să găsiți locația tastând:
```
whereis bash
```
(în special dacă folosiți C shell);

Dacă aceasta nu funcționează, încercați:
```
whence bash
```
```
which bash
```
sau această comandă mai complexă:
```
grep bash /etc/passwd | awk -F: '{print $7}' | sort -u
```

Ar trebui să vedeți un răspuns de forma:
```
/bin/bash
```
sau
```
/usr/local/bin/bash
```

## Instalarea bash ca shell de login
Pentru a instala bash ca shell de login, tastați:
```
chsh bash-nume
```
unde bash-nume este răspunsul primit la comanda whereis (sau orice altceva a funcționat). De exemplu:
```
% chsh /usr/local/bin/bash
```
Veți primi fie un mesaj de eroare care spune că shell-ul este invalid, fie vi se va cere parola. 
Tastați parola, apoi deconectați-vă și reconectați-vă pentru a începe să folosiți bash.

# Utilizarea interactivă a shell-ului
Când folosiți shell-ul interactiv, participați la o sesiune de login care începe atunci când vă conectați și se termină atunci când tastați:
```
exit
```
sau
```
logout
```
sau apăsați: 
```
CTRL-D.
```

În timpul unei sesiuni de login, tastați comenzi în shell; acestea sunt linii de text care se termină cu `RETURN` și pe care le introduceți în terminalul sau stația dvs. de lucru.

Implicit, shell-ul vă solicită fiecare comandă printr-un șir informativ urmat de semnul dolar `$`, deși, așa cum veți vedea în Capitolul 3, întregul prompt poate fi modificat.

# Comenzi, argumente și opțiuni

Liniile de comandă ale shell-ului constau din unul sau mai multe cuvinte, separate pe linie prin spații sau TAB-uri. Primul cuvânt de pe linie este comanda. Restul cuvintelor (dacă există) sunt argumente (numite și parametri) ale comenzii, adică nume de obiecte asupra cărora comanda va acționa.
De exemplu, linia de comandă:
```
lp myfile
```
constă din comanda 
```
lp
```
ce semnifică: tipărește un fișier; și un singur argument:
```
myfile
```
Comanda `lp` tratează `myfile` ca fiind numele fișierului care trebuie tipărit. Argumentele sunt adesea nume de fișiere, dar nu neapărat: în linia de comandă:
```
mail cam
```
programul `mail` tratează `cam` ca fiind numele utilizatorului căruia i se va trimite mesajul.
O opțiune este un tip special de argument care oferă comenzii informații specifice despre ce trebuie să facă. Opțiunile constau de obicei dintr-un minus urmat de o literă; spunem „de obicei” pentru că aceasta este o convenție, nu o regulă strictă.
De exemplu:
```
lp -h myfile
```
conține opțiunea `-h`, care îi spune comenzii `lp` să nu tipărească pagina de *„banner”* înainte de fișier.

Uneori, opțiunile au propriile argumente. De exemplu:
```
lp -d lp1 -h myfile
```
are două opțiuni și un argument.

Prima opțiune este `-d lp1`, ceea ce înseamnă *„Trimite ieșirea către imprimanta (destinația) numită lp1.”* 

A doua opțiune și argument sunt la fel ca în exemplul anterior.
