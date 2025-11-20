# Breviar de Bash

Bash, un program informatic al cărui nume 
constă din acronimul 
[expresiei](https://www.gnu.org/software/bash/manual/bash.html#What-is-Bash_003f-1) 
**B**ourne **A**gain **sh**ell, este un 
[interpretor de comenzi](https://www.gnu.org/software/bash/manual/bash.html#What-is-a-shell_003f-1)
(în engleză, 
[shell](http://www.catb.org/jargon/html/S/shell.html)) 
pe care îl întâlnim ca interpretor **prestabilit**, 
respectiv 
[de logare](https://learning.lpi.org/en/learning-materials/102-500/105/105.1/105.1_01/) 
(în engleză, *login shell*), într-o 
[sesiune de lucru](https://man.openbsd.org/ssh#DESCRIPTION) 
cu sistemul de operare
[GNU/Linux](https://www.gnu.org/gnu/linux-and-gnu.html).

Bash a fost construit de 
[Brian Fox](https://en.wikipedia.org/wiki/Brian_Fox_(programmer)) 
și este administrat de 
[Chet Ramey](https://tiswww.case.edu/php/chet/).

Următoarea comandă, executată 
[din](https://www.gnu.org/software/bash/manual/bash.html#Command-Execution-Environment) 
interpretorul Bash,
ne precizează 
[versiunea](https://www.gnu.org/software/bash/manual/bash.html#index-BASH_005fVERSION) 
acestuia:

```bash
echo $BASH_VERSION
```

Este folosită o 
[variabilă de interpretor](https://www.gnu.org/software/bash/manual/bash.html#Shell-Variables-1),
adică o sintagmă construită cu **termeni prestabiliți** 
(în cazul de față) și 
[prefațată](https://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion-1) 
cu 
[simbolul &#36;](https://learning.lpi.org/en/learning-materials/010-160/2/2.1/2.1_02/).

> [!Note]
> Aceeași informație, dar însoțită de un 
> [text informativ](https://www.gnu.org/software/bash/manual/bash.html#Invoking-Bash-1),
> este disponibilă ca rezultat al executării comenzii:
>
> ```bash
> bash --version
> ```

O comandă compusă, bazată pe cunoașterea 
[formatului](https://en.wikipedia.org/wiki/Delimiter-separated_values)
[înregistrărilor](http://www.catb.org/~esr/writings/taoup/html/ch05s02.html) 
dintr-o 
[bază de date fișier](https://en.wikipedia.org/wiki/Flat-file_database),
ne permite localizarea aplicației **bash**:

```bash
grep bash /etc/passwd  \
| awk -F: '{print $7}' \
| sort -u \
# după C. Newham & B. Rosenblatt, Learning the bash Shell, 3rd ed.
```

Baza de date interogată astfel este 
[/etc/passwd](https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/).

***

> VA URMA
