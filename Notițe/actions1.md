# Conținutul fișierului YAML al unei acțiuni GitHub

- [Declanșare manuală](#declanșare-manuală)

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
va declanșa o **rulare** (în engleză, *run*) 
a fluxului de lucru.

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

## Declanșare manuală

Un eveniment aparte este al declanșării 
[manuale](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#workflow_dispatch) 
a unei rulări a fluxului de lucru, cu numele
de `workflow_dispatch`, adică o comandă 
transmisă rapid, o **expediere** de mesaj sau
trimiterea unei **depeșe** (termen scos din uz, 
de la englezescul *dispatch*).

Îl putem insera în script în oricare din formele:

- tipică

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

 - cu precizarea tipurilor de date:

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

Îi putem adăuga date de intrare:

```yaml
name: Comanda manuală cu date de intrare
on: 
  workflow_dispatch:
    inputs:
      opțiunile_mele:
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
               ${{ inputs.opțiunile_mele }}.
```

Rezultatul acțiunii GitHub este disponibil în 
[fișierele de jurnal](https://docs.github.com/en/actions/how-tos/monitor-workflows/use-workflow-run-logs#viewing-logs-to-diagnose-failures)
ale rulării.

***

VA URMA
