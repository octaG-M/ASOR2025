# Ce este YAML-ul?

- [Elemente de YAML](#elemente-de-yaml)
  - Structuri primitive de date
    - [Scalari](#scalari)
    - [Dicționare](#dicționare)
    - [Tablouri](#tablouri)
  - [Etichete](#etichete)

Datele, produse de diverse programe, sunt fie 
**stocate** în 
[unități de memorie](https://en.wikipedia.org/wiki/Computer_data_storage#Primary)
fie **transmise** unor 
[echipamente periferice](https://en.wikipedia.org/wiki/Peripheral).
Din acest motiv, ele trebuie **preparate** pentru 
a fi ușor de memorat, respectiv de transportat. 
Un atare tratament al datelor poartă numele (generic) de 
[serializare](https://en.wikipedia.org/wiki/Serialization), 
denumiri specifice anumitor limbaje de programare fiind:

- **punerea la murat** din Python (în engleză,
  [pickle](https://docs.python.org/3/library/pickle.html))
- **alinierea la comandă** din C\# (în engleză,
  [marshalling](https://learn.microsoft.com/en-us/dotnet/standard/native-interop/type-marshalling)).

[YAML](https://en.wikipedia.org/wiki/YAML)-ul
este un limbaj de serializare a datelor ale cărui 
coduri-sursă sunt **ușor de citit** de către oameni
și al cărui nume constituie un 
[acronim recursiv](https://en.wikipedia.org/wiki/Recursive_acronym):
[YAML-ul Altceva-i decât un Marcaj de Limbaj](https://yaml.org/spec/1.2.2/#chapter-1-introduction-to-yaml).

YAML-ul a fost inventat de către 
[Clark Evans](https://clarkevans.com/),
[Oren Ben-Kiki](http://ben-kiki.org/oren/)
și
[Ingy döt Net](https://yamlscript.org/ingydotnet/).
El constituie o 
[extensie](https://yaml.org/spec/1.2.2/#12-yaml-history) 
a formatului de date 
[JSON](https://en.wikipedia.org/wiki/JSON).


[Procesorul](https://yaml.org/spec/1.2.2/#processes-and-models) 
(de) YAML este acea unealtă informatică responsabilă de 
**traducerea** datelor, scrise în 
[formatul YAML](https://yaml.org/spec/1.2.2/#representing-native-data-structures),
într-un 
[flux de caractere](https://yaml.org/spec/1.2.2/#323-presentation-stream) 
specific unei 
[platforme de calcul](https://en.wikipedia.org/wiki/Computing_platform).

Un procesor de YAML care **emite** 
[obiecte JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) 
este 
[JS-YAML](https://nodeca.github.io/js-yaml/). 
Un **parser** oficial de YAML, scris în JavaScript, se găsește 
[aici](https://play.yaml.io/main/javascript).
Un **linter** pentru YAML, realizat în Python, este disponibil
[aici](https://github.com/adrienverge/yamllint). El verifică
un set considerabil de 
[reguli](https://yamllint.readthedocs.io/en/stable/rules.html).

> [!Note]
> Un 
> [linter online](https://www.yamllint.com/), 
> cu 
> [autor necunoscut](https://lookup.icann.org/en/lookup), 
> este recomandat în 
> [învață X în Y minute](https://learnxinyminutes.com/yaml/).
> Acesta folosește (numai) un **arbore sintactic concret** 
> ([CST](https://en.wikipedia.org/wiki/Parse_tree)) la
> [construcția](https://www.yamllint.com/packed.js) 
> fluxului de 
> [documente YAML](https://yaml.org/spec/1.2.2/#91-documents).

## Elemente de YAML

Instrucțiunile care urmează alcătuiesc un necesar **minimal**.
Prezentări utile, cu (multe alte) detalii, pot fi citite în 
[învață X în Y minute](https://learnxinyminutes.com/yaml/),
respectiv în
[YAML basics in Kubernetes](https://developer.ibm.com/tutorials/yaml-basics-and-usage-in-kubernetes/).

Codul-sursă YAML este o succesiune de **documente**, adică de 
blocuri de text încadrate de seturi de **câte trei** 
[caractere](https://yaml.org/spec/1.2.2/#indicator-characters)
`-` (prefix), respectiv `.` (sufix):

```yaml
%YAML 1.2       # opțional: o directivă YAML
---             # prefix
blocul de text
...             # sufix
```

**Opțional**, înaintea prefixului poate fi inserată o
[directivă](https://yaml.org/spec/1.2.2/#681-yaml-directives).
Ea îl informează pe procesor despre **specificația** pe
care o respectă documentul. În lipsa directivei YAML,
se presupune că documentul urmează versiunea 
[1.2](https://yaml.org/spec/) 
a specificației.

Codul-sursă format 
dintr-[un singur document](https://yaml.org/spec/1.2.2/#bare-documents) 
nu necesită nici prefix nici sufix.

Caracterul `#` marchează începutul unui 
[comentariu](https://yaml.org/spec/1.2.2/#3233-comments). 
Evident, comentariile nu vor apărea în rezultatul procesării.

[Blocul de text](https://yaml.org/spec/1.2.2/#21-collections) 
dintr-un document YAML conține o **succesiune** de 
[structuri de date](https://en.wikipedia.org/wiki/Data_structure) 
native, exprimate cu caractere Unicode
[afișabile](https://yaml.org/spec/1.2.2/#character-set).
Aceste structuri pot fi redate prin combinarea a trei 
structuri de date **primitive**:

- [scalarul](https://yaml.org/spec/1.2.2/#scalars)
  ([șirul de caractere](https://en.wikipedia.org/wiki/String_literal) 
  ori **numărul**)
- [dicționarul](https://yaml.org/spec/1.2.2/#mapping) 
  (în engleză, *mapping*, 
  [hash](https://en.wikipedia.org/wiki/Hash_table), 
  *dictionary*)
- [tabloul](https://yaml.org/spec/1.2.2/#sequence) 
  (în engleză, *sequence*, 
  [array](https://en.wikipedia.org/wiki/Array_(data_structure)), 
  [list](https://en.wikipedia.org/wiki/Linked_list)).

Fiecare structură de date primitivă constituie un 
[nod](https://yaml.org/spec/1.2.2/#nodes) 
YAML. Astfel, ne referim la structura de date respectivă
ca la **conținutul** nodului. 
Opțional, nodul posedă și o 
[etichetă](https://yaml.org/spec/1.2.2/#resolved-tags) 
(în engleză, *tag*) care 
descrie **setul de valori** pe care le poate lua conținutul 
nodului, respectiv o
[ancoră](https://yaml.org/spec/1.2.2/#anchors-and-aliases)
(în engleză, *anchor*) care ne permite evitarea repetițiilor
prin utilizarea de **pseudonime**.

Nodurile construite pe baza altor noduri, adică dicționarele
și tablourile, sunt denumite 
[colecții](https://yaml.org/spec/1.2.2/#representation-graph).

## Scalari

Scalarii pot fi exprimați în mai multe **stiluri**. Astfel,
[stilul bloc](https://yaml.org/spec/1.2.2/#block-style-productions),
care se bazează pe 
[indentare](https://yaml.org/spec/1.2.2/#indentation-spaces) 
pentru a descrie structura unui conținut, se compune din 
(sub)[stilul literal](https://yaml.org/spec/1.2.2/#literal-style) 
și din
(sub)[stilul împăturit](https://yaml.org/spec/1.2.2/#folded-style).

```yaml
---
# substilul literal este dat de caracterul indicator |
# se folosește aceeași indentare cu caractere ' '
# se păstrează rândurile 
|       
  Ana are mere. 
  Mama face dulceață.
  Afară e frig.
...
---
# substilul împăturit este dat de caracterul indicator >
# primele două rânduri se comasează
>       
  Ana are mere. 
  Din ele, mama va face dulceață.

  Afară e frig.
...
```

Stilul 
[flux](https://yaml.org/spec/1.2.2/#flow-scalar-styles),
de exprimare a unui scalar, este compus din 
(sub)[stilul fără ghilimele](https://yaml.org/spec/1.2.2/#plain-style),
din
(sub)[stilul cu apostrofuri](https://yaml.org/spec/1.2.2/#single-quoted-style)
și din
(sub)[stilul cu ghilimele](https://yaml.org/spec/1.2.2/#double-quoted-style).
Doar ultimul substil permite 
[escaparea](https://yaml.org/spec/1.2.2/#escaped-characters) 
caracterelor.

```yaml
---
# substilul direct (fără ghilimele)
123
...
---
# substilul cu apostrofuri (ghilimele simple)
'Ana are mere.'
...
---
# substilul cu ghilimele (duble)
"Ana are mere.\nAfară e frig."
...
```

## Dicționare

[Dicționarele](https://yaml.org/spec/1.2.2/#mapping) 
sunt ansambluri **neordonate** de dublete **cheie**-**valoare**,
unde cheile și valorile desemnează noduri YAML oarecare, 
cu condiția ca **fiecare cheie să fie unică** într-un 
dicționar.

Dubletul cheie-valoare este exprimat intercalând 
caracterele 
[două-puncte-spațiu](https://yaml.org/spec/1.2.2/#separation-spaces) 
`: `&nbsp; între cheie și valoare:

```yaml
---
cheia1: valoarea1
cheia2: valoarea2
...
---
textul1: |
           Ana
           are
           mere.
textul2: "Afară e frig."
...
```

> [!Note]
> Prezența caracterului
> [spațiu](https://yaml.org/spec/1.2.2/#white-space-characters) 
> ne permite utilizarea caracterului `:`
> la construcția valorii. De exemplu,
>
> ```yaml
> cheia: :valoarea
> ```
>
> se transformă în obiectul JavaScript
>
> ```javascript
> { cheia: ':valoarea' }
> ```
> Utilitatea acestui construct este evidentă
> în cazul **datelor de timp**:
>
> ```yaml
> momentul sosirii: 2024:11:02 10:25:12 # AAAA:LL:ZZ HH:MM:SS
> ```

Dicționarele folosesc stilurile 
[bloc](https://yaml.org/spec/1.2.2/#822-block-mappings)
și
[flux](https://yaml.org/spec/1.2.2/#742-flow-mappings):

```yaml
---
# dicționar în bloc
cheia1: valoarea1
cheia2: valoarea2
...
---
# dicționar în flux
{ cheia1: valoarea1, cheia2: valoarea2 }
...
```

Utilizarea unei 
[etichete predefinite](https://yaml.org/spec/1.2.2/#10111-generic-mapping), 
într-un dicționar, se realizează cu prefixul `!!`:

```yaml
---
!!map
# formatul bloc
cheia1: valoarea1
cheia2: valoarea2
...
---
!!map
# formatul flux
{ cheia1: valoarea1,
  cheia2: valoarea2 }
...
```

Introducerea unui pseudonim (în engleză, *alias*)
întrebuințează prefixele `&` (pentru
[ancorarea](https://yaml.org/spec/1.2.2/#692-node-anchors) 
unui nume de un nod) și `*` (pentru 
[referirea](https://yaml.org/spec/1.2.2/#alias-nodes)
la nodul ancorat prin respectivul nume):

```yaml
!!map
cheia1: &pseudonim valoarea1  # ancorăm valoarea1
cheia2: valoarea2
cheia3: *pseudonim            # folosim pseudonimul
                              # pentru a-i da cheii
                              # cheia3 valoarea
                              # valoarea1
```

Pentru a 
[amâna](https://yaml.org/spec/1.2.2/#resolved-tags) 
atribuirea de 
[valori](https://yaml.org/spec/1.2.2/#example-empty-content) 
propriu-zise unui set de chei, adică a le atribui 
**valoarea nulă**, folosim caracterul `?` sub forma
**semn-de-întrebare-spațiu**:

```yaml
---
!!map {
? cheia1, # adică cheia1: null
? cheia2
}
...
---
!!map {
? cheia3: !!str "", # adică cheia3: ''
                    # str este eticheta predefinită
                    # a unui șir de caractere
? cheia4
}
...
```

[Caracterul](https://yaml.org/spec/1.2.2/#example-flow-mapping-entries) 
[indicator](https://yaml.org/spec/1.2.2/#rule-c-mapping-key) 
`?` poate fi utilizat și pentru a-i anunța procesorului 
prezența unei **chei complexe**:

```yaml
!!map {
? !!map { cheia1: valoarea1, cheia2: valoarea2 }: valoarea3,
cheia4: valoarea4
}
```

## Tablouri

[Tablourile](https://yaml.org/spec/1.2.2/#sequence) 
sunt ansambluri **ordonate** de noduri YAML, care 
**se pot repeta**.

Elementele unui tablou sunt prefixate de dubletul
[cratimă-spațiu](https://yaml.org/spec/1.2.2/#block-sequences)
`- `:

```yaml
---
- elementul1
- elementul2
- elementul3
...
---
- elementul4
-                   # tablou în tablou
  - elementul5
  - elementul6
  - elementul7
-                   # dicționar în tablou
  cheia1: valoarea1
  cheia2: valoarea3
  cheia3: valoarea3
                    # șir de caractere în tablou
- !!str |-          # nu se inserează "\n"
  Salut!
  Bine ai venit!
...
```

Am folosit **caracterul indicator** `-`, care
anunță 
[eliminarea](https://yaml.org/spec/1.2.2/#block-chomping-indicator) 
caracterului(or) de trecere pe un rând nou 
(în engleză, *chomping*) de la **finalul** 
unui scalar:

```yaml
- un text împăturit: >-
    Ca de fiecare dată, 
    suntem atenți
    la noua sintaxă.

    Desigur, 
    nu neglijăm 
    nici morfologia.
- un text literal: |-
    instrucțiunea1
    instrucțiunea2

    instrucțiunea3
```

Tablourile sunt scrise în oricare din stilurile 
[bloc](https://yaml.org/spec/1.2.2/#821-block-sequences) 
și 
[flux](https://yaml.org/spec/1.2.2/#741-flow-sequences):

```yaml
---
# tablou în bloc
- !!str 'Bună ziua!'
- !!map { cheia1: valoarea1,
  cheia2: valoarea2 }
- 123
- !!seq [ 4, 5, 6 ]           # eticheta predefinită
                              # pentru tablouri
- - 7
  - 8
  - 9
...
---
# tablou în flux
[ numele-comenzii1,
  opțiunea1-a-comenzii1,
  opțiunea2-a-comenzii1,
  numele-comenzii2-care-depinde-de-comanda1,
  opțiunea-comenzii2 ]
...
```

## Etichete

Nodurile YAML se împart, după seturile de valori
care le sunt permise conținutului lor, în:
- **etichetate**, adică având etichete
  [rezolvate](https://yaml.org/spec/1.2.2/#tag-resolution), 
  deci cu tipurile de conținut **furnizate** de 
  către specificația YAML:
  - tipuri de date **generice**, făcând parte din 
    [schema de siguranță](https://yaml.org/spec/1.2.2/#failsafe-schema)
    a specificației și înțelese de către *orice* 
    procesor de YAML:
    - **str**, **map** și **seq**
  - tipuri de date ale formatului 
    [JSON](https://yaml.org/spec/1.2.2/#json-schema),
    înțelese de către *majoritatea* procesoarelor de YAML:
    - **null**, **bool**, **int** și **float**
  - tipuri de date ale specificației 
    [1.1](https://yaml.org/type/index.html):
    - [binary](https://yaml.org/type/binary.html),
      [merge](https://yaml.org/type/merge.html),
      [omap](https://yaml.org/type/omap.html),
      [pairs](https://yaml.org/type/pairs.html),
      [set](https://yaml.org/type/set.html),
      [timestamp](https://yaml.org/type/timestamp.html),
      [value](https://yaml.org/type/value.html),
      [yaml](https://yaml.org/type/yaml.html)
- **neetichetate**, adică având conținuturi **specifice** 
  [aplicației](https://yaml.org/spec/1.2.2/#processes-and-models) 
  căreia îi sunt destinate datele din documentul YAML și
  a căror înțelegere cade în sarcina acesteia
- **nerecunoscute**, adică având etichetele
  [nerezolvate](https://yaml.org/spec/1.2.2/#recognized-and-valid-tags).

```yaml
șir de caractere:             !!str ""
dicționar gol:                !!map {}
tablou gol:                   !!seq []
tipul nul:                    !!null null
valoarea de adevăr 1:         !!bool true
valoarea de adevăr 0:         !!bool false
număr întreg:                 !!int 123
număr cu virgulă:             !!float 45.67
? valori specifice aplicației 
```

***

> Când datele sunt ușor de văzut și de înțeles,
> programarea pare mai simplă.
> (YAML Spec., 
> [Capitolul 1](https://yaml.org/spec/1.2.2/#chapter-1-introduction-to-yaml))
