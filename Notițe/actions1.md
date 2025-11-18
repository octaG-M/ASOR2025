# Conținutul fișierului YAML al unei acțiuni GitHub

- [Declanșarea manuală a execuției](#declanșarea-manuală-a-execuției)
  - [Folosirea unui nume de rulare](#folosirea-unui-nume-de-rulare)
- [Sarcinile fluxului](#sarcinile-fluxului)

Automatizarea oferită de platforma GitHub
presupune configurarea unui 
[flux de lucru](https://docs.github.com/en/actions/concepts/workflows-and-actions/workflows)
(în engleză, *workflow*).

Pentru aceasta, folosim un 
[dicționar](./introducere_in_yaml.md#dicționare)
de date ale cărui **chei** sunt 
[cuvinte predefinite](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax).

Deși dicționarele sunt **neordonate**, începem cu
atribuirea unui 
[nume sugestiv](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax#name)
pentru fluxul de lucru. Cheia acestuia este cuvântul predefinit `name`:

```yaml
name: nume-sugestiv # sunt permise spațiile goale între cuvinte
```

Ca să fie realizate sarcini în mod automat, trebuie
să precizăm:

- cel puțin un 
  [eveniment](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows) 
  GitHub 
- un 
  [declanșator](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax#on)
  (în limba engleză, *trigger*). 

Declanșatorul este dat prin cuvântul predefinit `on`:

  ```yaml
  # continuare
  on:
    evenimentul
  ```

Astfel, producerea evenimentului ``evenimentul`` 
va declanșa o **execuție** (în engleză, *run*),
ori o **rulare**, a fluxului de lucru.

Dacă dorim ca sarcinile să fie îndeplinite atunci
când intervin unul sau
[mai multe evenimente](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax#using-multiple-events), 
vom folosi un 
[tablou](./introducere_in_yaml.md#tablouri) 
de date, exprimat în stilul flux:

```yaml
# continuare
on:
  [ evenimentul1, evenimentul2 ]
```

## Declanșarea manuală a execuției

Un eveniment aparte este cel al declanșării 
[manuale](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#workflow_dispatch) 
a unei execuții a fluxului de lucru, cu numele
de `workflow_dispatch`, termen predefinit care
sugerează o solicitare transmisă rapid, o 
**expediere** de mesaj sau trimiterea unei 
**depeșe** (cuvânt scos din uz, de la englezescul 
*dispatch*).

Evenimentul se inserează în script cu oricare 
din formele:

- tipică, precum

  ```yaml
  name: Comanda manuală uzuală
  on: 
    workflow_dispatch:
  jobs: 
    mesagerie: 
      runs-on: ubuntu-latest
      steps:
        - run: echo Salut uzual!
  ```

 - cu precizarea tipurilor de date, cum ar fi

   ```yaml
   !!map {
     name: !!str "Comanda manuală cu tipuri de date",
     on:   !!str "workflow_dispatch",
     jobs: !!map { 
             mesagerie: !!map { 
                          runs-on: !!str "ubuntu-latest", 
                          steps:   !!seq [ 
                                     run: !!str "echo Salut cu tipuri de date!" 
                                   ] 
                        } 
           }
   }
   ```

Rezultatul acțiunii GitHub este disponibil în 
[fișierele de jurnal](https://docs.github.com/en/actions/how-tos/monitor-workflows/use-workflow-run-logs#viewing-logs-to-diagnose-failures)
ale rulării.

Evenimentului `workflow_dispatch` îi putem adăuga 
[date de intrare](https://github.blog/changelog/2021-11-10-github-actions-input-types-for-manual-workflows/) 
folosind cuvântul-cheie predefinit `inputs`:

```yaml
name: Comanda manuală cu date de intrare
on: 
  workflow_dispatch:
    inputs:
      optiunile_mele:
        description: 'Ce alegeți?'
        required:    true
        type:        choice
        options:
                     - 'unu'
                     - 'doi'
                     - 'trei'
jobs: 
  mesagerie: 
    runs-on: ubuntu-latest
    steps:
      - run: >
               echo Salut!
               Am optat pentru
               ${{ inputs.optiunile_mele }}.
```

### Folosirea unui nume de rulare

O anumită execuție a fluxului de lucru, datorată
unui eveniment important, poate fi evidențiată
printr-un 
[nume de rulare](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax#run-name), 
ori **de execuție**, 
<span id="referire_la_jobs">exprimat</span> 
de constructul predefinit `run-name`:

```yaml
name:   >-
          Comanda manuală 
          cu date de intrare
          și nume-de-rulare
run-name: Testarea opțiunii ${{ inputs.optiunile_mele }}
on: 
  workflow_dispatch:
    inputs:
      optiunile_mele:
        description: 'Ce alegeți?'
        required:    true
        type:        choice
        options:
                     - 'unu'
                     - 'doi'
                     - 'trei'
jobs: 
  mesagerie: 
    runs-on: ubuntu-latest
    steps:
      - run: >
               echo Salut!
               Am optat pentru
               ${{ inputs.optiunile_mele }}.
```

## Sarcinile fluxului

Prin 
[sarcină](https://docs.github.com/en/actions/get-started/understand-github-actions#jobs) 
(în engleză, *job*) a fluxului de lucru
înțelegem un set de **pași** (în engleză, *step*) 
în cadrul cărora sunt descrise diverse 
[activități](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax#jobsjob_idsteps) 
(în engleză, *task*) care urmează a fi executate pe 
mașina virtuală. Activitățile sunt:

- scripturi de interpretor (în engleză, *shell script*)
- alte acțiuni GitHub.

Fiecare sarcină va fi executată pe propria ei 
[mașină virtuală](https://docs.github.com/en/actions/reference/runners/github-hosted-runners#standard-github-hosted-runners-for-public-repositories).
Mașina virtuală, creată exclusiv pentru rularea 
pașilor sarcinii, este un 
[furnizor](https://github.com/actions/runner)
numit 
[executor](https://docs.github.com/en/actions/get-started/understand-github-actions#runners) 
(în engleză, *runner*).

Sarcinile sunt grupate într-un dicționar de date cu
numele predefinit `jobs`. Pașii de lucru ai unei
sarcini formează un tablou de date cu numele predefinit
`steps`. Perechea cheie-valoare, din dicționarul de
date la care ne referim folosind numele dat de noi
al sarcinii (vezi, 
[deasupra](./actions1.md#referire_la_jobs), 
sarcina `mesagerie`), în care este introdusă informația 
privitoare la mașina virtuală are drept cheie sintagma 
predefinită 
[runs-on](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax#jobsjob_idruns-on).

Sarcina următoare, `informatiile`, trebuie să parcurgă
doi pași:

- Primul pas apelează, utilizând cuvântul predefinit 
  [uses](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax#jobsjob_idstepsuses), 
  acțiunea GitHub 
  [checkout](https://github.com/marketplace/actions/checkout),
  în urma căreia conținutul unui proiect GitHub va fi
  disponibil pe mașina virtuală. Această **punere la dispoziție**
  (în engleză, *checkout*) a detaliilor folosește un 
  [termen predefinit](https://git-scm.com/docs/git-checkout) 
  din terminologia celui mai cunoscut (IMHO)
  [sistem de control al versiunii](https://en.wikipedia.org/wiki/Version_control) 
  unui software, adică 
  [Git](https://git-scm.com/). 
- Cel de-al doilea pas constă din rularea, cu termenul predefinit 
  [run](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax#jobsjob_idstepsrun),
  a unui script de interpretor. Aici, întrebuințăm
  [variabila de mediu](https://docs.github.com/en/actions/reference/workflows-and-actions/variables#default-environment-variables) 
  `GITHUB_WORKSPACE` pentru a ne referi la 
  [calea](https://en.wikipedia.org/wiki/Path_(computing)) 
  proiectului, respectiv o 
  [expresie](https://docs.github.com/en/actions/reference/workflows-and-actions/expressions), 
  dată de constructul `${{ nume-de-variabilă }}`, pentru a 
  introduce calea în script.

```yaml
name: Conținutul proiectului meu
on: 
  workflow_dispatch: !!null null
jobs: 
  informatiile: 
    runs-on: ubuntu-latest
    steps:
      - name: prepararea-proiectului (Git checkout)
        uses: actions/checkout@v5 
      - name: construcția-informației
        run:  |
               echo "Conținutul proiectului:"
               echo "`ls -la ${{ github.workspace }} | head -n 32`"
```
