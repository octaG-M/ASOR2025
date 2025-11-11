# Conținutul fișierului YAML al unei acțiuni GitHub

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

Astfel, evenimentul ``evenimentul`` va declanșa o **rulare** 
(în engleză, *run*) a fluxului de lucru.

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

***

VA URMA
