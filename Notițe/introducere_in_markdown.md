# Ce este Markdown-ul?

- [CommonMark](#commonmark)
- [Markdown-ul de pe platforma GitHub](#markdown-ul-de-pe-platforma-github)
- [Elemente de Markdown](#elemente-de-markdown)

Textul pe care îl citim într-o pagină **web** 
(o știre recentă, descrierea unui fenomen, șamd.) a fost
mai întâi scris într-un editor de text și apoi
**adnotat** (sau **marcat** ori **formatat**) pentru
ca *afișarea* lui să includă culori, sublinieri,
fonturi diverse și multe alte *accesorii* ale
prezenței sale online. Marcajele (în engleză,
[markup](https://en.wikipedia.org/wiki/Markup_language)) 
sunt realizate în 
[HTML](https://en.wikipedia.org/wiki/HTML).

Markdown(ul) este un limbaj de **formatare** a textului,
care ne permite să fim (mult mai) *productivi* atunci când
scriem un document pe care intenționăm să-l **structurăm**,
adică să-i organizăm conținutul în capitole, secțiuni, 
paragrafe ce urmează să fie accesate prin 
[hiper](https://en.wikipedia.org/wiki/Hyperlink)-legături: 
cu alte cuvinte, o pagină **web**. 

Deși numele său încearcă să ne convingă că este un limbaj
*simplist* (**down**), prin opoziție cu complicațiile de
marcaj (**up**) din HTML, unii 
[autori](https://learnxinyminutes.com/markdown/) 
îl socotesc o **extensie** a acestuia: putem insera 
[instrucțiuni HTML](https://spec.commonmark.org/0.31.2/#html-blocks) 
în orice fragment de text scris în Markdown.

Iată o comparație între HTML:

```html
<strong>adnotare</strong>
```

și Markdown:

```markdown
**adnotare**
```

Programul care **traduce** textul adnotat în Markdown 
(text la care ne referim, adesea, cu apelativul 
[cod-sursă](https://en.wikipedia.org/wiki/Source_code)) 
în HTML se numește **procesor** (de Markdown).

Limbajul Markdown a fost inventat de 
[John Gruber](https://daringfireball.net/projects/markdown/)
și instrucțiunile sale pot fi testate 
[aici](https://daringfireball.net/projects/markdown/dingus).
Infrastructura folosită de *fereastra* de testare este denumită,
atunci când ne referim la Markdown, *flecușteț* (în engleză, colocvial,
[dingus](https://talk.commonmark.org/t/origin-of-the-usage-for-dingus/1226)).

## CommonMark

Anumite ambiguități, descoperite de către utilizatori în sintaxa 
inițială a Markdown-ului, au fost clarificate prin introducerea unei 
**specificații** (sau **standardizări**) a acestuia, sub numele de 
[CommonMark](https://spec.commonmark.org/0.31.2/).

Un procesor de [M↓](https://github.com/dcurtis/markdown-mark) 
(semnul grafic al CommonMark-ului), realizat în JavaScript, 
poate fi încercat în fereastra de aici:
[dingus](https://spec.commonmark.org/dingus/). Codul-sursă al implementării 
specificației (folosit de acest procesor) este disponibil
[aici](https://github.com/commonmark/commonmark.js).

Alt procesor de Markdown, avansat, este 
[remark](https://remark.js.org/), în jurul său fiind organizată
[infrastructura de traducere](https://docs.github.com/en/contributing/writing-for-github-docs/using-markdown-and-liquid-in-github-docs#about-using-markdown-and-liquid-in-github-docs) 
în HTML a codurilor-sursă Markdown de pe platforma Github.

Aceste procesoare 
[parsează](https://en.wikipedia.org/wiki/Parsing) 
codul-sursă Markdown întâlnit și îi construiesc 
**arborele sintactic abstract** 
([AST](https://en.wikipedia.org/wiki/Abstract_syntax_tree)), apoi, 
prin
[parcurgerea](https://en.wikipedia.org/wiki/Tree_traversal) 
sa, 
[emit](https://en.wikipedia.org/wiki/Code_generation_(compiler)) 
codul-sursă **țintă**: HTML (pentru includerea în pagina web) ori XML 
(o reprezentare a AST-ului).

Un 
[linter](https://en.wikipedia.org/wiki/Lint_(software))
pentru Markdown este disponibil 
[aici](https://github.com/markdownlint/markdownlint),
el verificând un set cuprinzător de 
[reguli](https://github.com/markdownlint/markdownlint/blob/main/docs/RULES.md).

## Markdown-ul de pe platforma GitHub

Pe platforma GitHub este folosită o **extindere** a Markdown-ului, 
respectând specificația CommonMark, cu numele de 
**Markdown cu aromă de GitHub** 
([GFM](https://github.github.com/gfm/#what-is-github-flavored-markdown-); 
în engleză,
[GitHub Flavored Markdown](https://docs.github.com/en/contributing/writing-for-github-docs/using-markdown-and-liquid-in-github-docs#about-using-markdown-and-liquid-in-github-docs)). 
Astfel, în această variantă de Markdown, există adnotări suplimentare 
pentru:

- [alerte](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#alerts)
- [tabele](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-tables)
- hiper-legături la [instrucțiuni administrative](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/autolinked-references-and-urls#issues-and-pull-requests)
- [colorarea cuvintelor-cheie](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#syntax-highlighting) 
  ale fragmentelor de cod-sursă
- [butoane de copiere](https://docs.github.com/en/contributing/writing-for-github-docs/using-markdown-and-liquid-in-github-docs#code-blocks-with-a-copy-button) 
  a unor fragmente de cod-sursă
- etichete (în engleză, *tag*) privind un 
  [sistem de operare](https://docs.github.com/en/contributing/writing-for-github-docs/using-markdown-and-liquid-in-github-docs#operating-system-tags) 
  ori o 
  [unealtă informatică](https://docs.github.com/en/contributing/writing-for-github-docs/creating-tool-switchers-in-articles#using-tool-tags)

șamd.

## Elemente de Markdown

Instrucțiunile care urmează alcătuiesc un necesar **minimal**.
Prezentări utile, cu (multe alte) detalii, pot fi citite în 
[învață X în Y minute](https://learnxinyminutes.com/markdown/),
respectiv în 
[Markdown Here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet). 

Titlurile 
([ATX](https://spec.commonmark.org/0.31.2/#atx-headings), vezi
[A. Swartz](http://www.aaronsw.com/2002/atx/))
sunt texte pe un rând, **prefixate** de caractere `#`:

```markdown
# Secțiune
## Subsecțiune
### Subsubsecțiune
```

Hiper-legăturile (linkurile) pot fi realizate atât cu adrese
([URL](https://en.wikipedia.org/wiki/URL))
**absolute** cât și cu adrese 
[relative](https://spec.commonmark.org/0.31.2/#link-destination):

```markdown
[textul hiper-legăturii](https://www.nume1.ro)
[textul hiper-legăturii](./programe/unealta2.py)
```

Pe platforma GitHub, adresele relative se exprimă în funcție de
rădăcina
[proiectului](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#relative-links).

[Stilizarea](https://spec.commonmark.org/0.31.2/#html-block) 
afișării unor fragmente de text permite:

1. șiruri de caractere **îngroșate**: 

   ```markdown
   **îngroșate**
   ```

2. cuvinte cu literele *aplecate* spre dreapta:  

   ```markdown
   *aplecate*
   ```

3. inserarea unor simboluri cu indici, *a<sub>n</sub>*
   și *e<sup>x</sup>*:

   ```markdown
   a<sub>n</sub> și e<sup>x</sup>
   ```

4. elemente de interes <ins>subliniate</ins>: 

   ```markdown
   <ins>subliniate</ins>
   ```

[Listele](https://spec.commonmark.org/0.31.2/#lists) sunt:

1. numerotate (ordonate; `<OL>` în HTML; în engleză, 
   *ordered*):  

   ```markdown
   1. primul item
   2. al doilea item
   3. al treilea item
   ```

2. nenumerotate (
   [dezordonate](https://en.wikipedia.org/wiki/HTML_element#Lists) 
   😊; `<UL>` în HTML; în engleză, *unordered*):  

   ```markdown
   - un item
   - alt item
   - încă un item
   ```

Pentru [fragmentele](https://spec.commonmark.org/0.31.2/#fenced-code-blocks) 
de cod, se recomandă să precizăm numele 
[limbajului de programare](https://github.com/highlightjs/highlight.js/blob/main/SUPPORTED_LANGUAGES.md) 
în care sunt scrise instrucțiunile respective:
 
   ~~~markdown
   ```numele-limbajului-de-programare
   o instrucțiune
   altă instrucțiune
   ```
   ~~~

Pe platforma Github, acestor fragmente li se pot adăuga: un 
**buton de copiere** (a instrucțiunilor), respectiv
[adnotări](https://docs.github.com/en/contributing/writing-for-github-docs/annotating-code-examples) 
în cazul codurilor complexe.

[Liniile orizontale](https://spec.commonmark.org/0.31.2/#thematic-breaks) 
de despărțire (`<HR/>` în HTML) necesită un marcaj format din 
**cel puțin trei** caractere:  

   ```markdown
   textul 1
  
   ---

   textul 2

   ***

   textul 3
   ```

[Citările de texte](https://spec.commonmark.org/0.31.2/#block-quotes) 
(`<blockquote>` în HTML), în care putem folosi 
marcaje Markdown, sunt **prefixate** de caracterul `>`:

   ```markdown
   > Lista de itemi pe care mi-ați trimis-o:
   > 
   > - reviste
   > - cărți
   > - caiete
   >
   ```

O linie de text *prea lungă* poate fi 
[ruptă](https://spec.commonmark.org/0.31.2/#hard-line-breaks) 
prin introducerea caracterului `\` (`<BR/>` în HTML) în 
locul unde trebuie realizată ruperea:

   ```markdown
   o linie prea\
   lungă
   ```
---

În concluzie, scrierea unui text folosind Markdown-ul trebuie
să fie la fel de simplă ca scrierea unui email:

> ...you should be able to just 
> [write as you do in email](http://www.aaronsw.com/2002/atx/intro)
> ([Aaron Swartz](https://en.wikipedia.org/wiki/Aaron_Swartz))
