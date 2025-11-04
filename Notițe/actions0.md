# Ce este o acțiune GitHub?

- [DevOps, IaC, GitOps](#devops-iac-gitops)
- [Github Actions](#github-actions)

Realizarea unui produs informatic presupune,
[în afară de](https://en.wikipedia.org/wiki/Software_testing)
scrierea **codului-sursă** într-un 
limbaj de programare sau în mai multe, 
[testarea](https://en.wikipedia.org/wiki/Test-driven_development)
[versiunii curente](https://en.wikipedia.org/wiki/Version_control) 
a acestuia pe diverse mașini/platforme de calcul.

## DevOps, IaC, GitOps

Sistemul de **control al versiunii** unui produs,
întrebuințat pe platforma GitHub, este 
[Git](https://git-scm.com/).
El permite:

- construcția unei **copii** a unui proiect 
  public, adică 
  realizarea unei 
  [bifurcări](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project.html#_forking_projects) 
  (în engleză, *fork*) a proiectului inițial 
  în contul GitHub personal
- adresarea, către autorii proiectului inițial, 
  a unei 
  [cereri de tragere la sursă](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project.html#_creating_a_pull_request) 
  (în engleză, *pull request*) a **modificărilor** aduse 
  unui proiect bifurcat anterior prin operații 
  **efectuate asupra copiei** din contul personal
- construcția de 
  [ramificații](https://git-scm.com/docs/user-manual.html#Documentation/user-manual.txt-branch)
  (sau **ramuri**; în engleză, *branch*) ale 
  oricărui proiect din contul GitHub personal
- realizarea de modificări **jurnalizate** ale 
  unui proiect din contul personal sub formă de
  [comiteri](https://git-scm.com/docs/user-manual.html#Documentation/user-manual.txt-commit)
  (în engleză, *commit*)
- modificarea unor comiteri din trecut, adică
  efectuarea unei 
  [așezări pe altă bază](https://git-scm.com/docs/git-rebase)
  (sau o **re-bazare**; în engleză, *rebase*) a proiectului
  din contul GitHub personal

șamd.

Prin legarea calculatorului personal, o 
mașină-[client](https://en.wikipedia.org/wiki/Client_(computing)),
la rețeaua de Internet, componentele fizice ale
[infrastructurii IT](https://en.wikipedia.org/wiki/IT_infrastructure)
necesare testării produsului pot fi înlocuite cu 
[componente virtuale](https://en.wikipedia.org/wiki/Hardware_virtualization),
ale căror caracteristici tehnice sunt indicate prin 
[blocuri de cod](https://www.redhat.com/en/topics/cloud-computing/what-is-iaas).
Această modalitate de a-i furniza clientului 
**infrastructura ca (pe un) serviciu**
([IaaS](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)) 
făcut de către un **furnizor** (în engleză, *server*) 
îl eliberează pe dezvoltatorul produsului informatic 
de luarea de decizii privind:

- tipul de **virtualizare** folosit la instalarea sistemului(or) 
  de operare în care se va desfășura testarea
- **serverele** fizice pe care se va realiza virtualizarea
- **mediile de stocare** a informației folosite/produse la testare
- **rețelele** de legătură între diversele echipamente electronice.

Dezvoltatorului îi rămâne să se pronunțe numai vizavi de:

- sistemul de operare
- [platformele](https://www.redhat.com/en/topics/middleware) 
  de aplicații și de comunicații (în engleză, 
  [middleware](https://en.wikipedia.org/wiki/Middleware))
- mediile de execuție (în engleză, 
  [runtime](https://en.wikipedia.org/wiki/Runtime_system))
- bazele de date
- uneltele informatice asociate proiectului propriu-zis.

> [!Note]
> Așadar, 
> [nevoile de calcul](https://en.wikipedia.org/wiki/Computer_cluster) 
> ale dezvoltatorului unui produs informatic îi sunt satisfăcute 
> acestuia prin 
> [servicii](https://en.wikipedia.org/wiki/Service-oriented_architecture)
> oferite de către diverse corporații, de îndată ce:
>
> - ele au fost descrise într-un 
>   [limbaj specificat de domeniu](https://en.wikipedia.org/wiki/Domain-specific_language)
> - le-a fost operaționalizată **plata** 
>   ([FinOps](https://www.finops.org/introduction/what-is-finops/))
>
> șamd.

De îndată ce s-au realizat servirea infrastructurii și 
operaționalizarea plății, dezvoltatorul se poate implica 
în parcurgerea 
[ciclului de dezvoltare](https://en.wikipedia.org/wiki/Software_development_process)
al proiectului informatic. De acum, intervin (adesea) 
schimbări în legătură cu oricare din deciziile luate 
la începutul dezvoltării proiectului, precum:

- schimbarea **drepturilor de utilizare** ale unei 
  unelte informatice
- încheierea **ciclului de exploatare** al unui 
  sistem de operare
- renunțarea la un **model de organizare** a datelor

șamd.

La operaționalizarea luării de decizii noi de către dezvoltator, 
adică la 
[operaționalizarea dezvoltării](https://github.com/resources/articles/what-is-sdlc#how-can-devops-be-integrated-into-the-sdlc)
(sau, pe scurt, la **dezvoltare și operații**), ne referim cu acronimul 
[DevOps](https://devops.com/the-evolution-of-devops/).
Un aspect esențial al DevOps-ului se referă la **metodologia**
utilizată de către dezvoltator cu privire la:

- **includerea** contribuțiilor curente ale membrilor echipei
  în baza de cod-sursă a proiectului, adică **integrarea**
  (în engleză, *integration*) noilor rezultate în produs
- **distribuirea** (în engleză, *delivery*) rezultatului 
  integrării către clienți (începând cu distribuirea către 
  [entuziaști](https://en.wikipedia.org/wiki/Early_adopter)).

Dacă se folosesc integrarea **continuă** de mici modificări
și distribuirea **imediată** a oricărei noutăți 
([reușite](https://www.atlassian.com/continuous-delivery/principles/pipeline)), 
atunci avem de a face cu metodologia 
[CI/CD](https://github.com/resources/articles/ci-cd).

> [!Caution]
> Litera **D** din acronimul CI/CD înseamnă atât 
> **distribuire** (în mediul de producție al 
> dezvoltatorului și **nu** către clienți) cât și 
> **lansare** (în engleză, *deployment*), termen 
> la care nu ne referim momentan. Această simplificare
> poate fi justificată prin generalitatea textului de față.

Modificările care survin pe durata ciclului de dezvoltare
a produsului informatic implică de multe ori și schimbarea
nevoilor de calcul ale dezvoltatorului. Operaționalizarea
procedurilor de **adaptare continuă** a infrastructurii IT 
la cerințele versiunii curente a produsului poartă numele
generic de 
[infrastructură (cerută furnizorului) sub formă de cod](https://www.redhat.com/en/topics/automation/what-is-infrastructure-as-code-iac), 
adică 
[IaC](https://opensource.com/article/19/7/infrastructure-code).

> [!Note]
> În particular, atunci când o astfel de 
> [operaționalizare a infrastructurii](https://www.atlassian.com/git/tutorials/gitops) 
> se folosește de capacitățile sistemului de control al 
> versiunii Git, spunem că avem de a face cu o
> [operaționalizare Git](https://github.com/weaveworks/awesome-gitops), 
> pe scurt [GitOps](https://codefresh.io/learn/gitops/).

## GitHub Actions

Pe platforma GitHub, putem exprima prin blocuri de cod
scrise în limbajul de serializare a datelor 
[YAML](./introducere_in_yaml.md)
o clasă de 
[obiecte administrative](https://github.com/marketplace?type=actions) 
dedicate punerii
în practică a metodologiei CI/CD, și anume
[acțiunile GitHub](https://docs.github.com/en/actions/get-started/understand-github-actions#actions).
Un exemplu de acțiune GitHub dedicată metodologiei GitOps
este disponibil 
[aici](https://github.com/Staffbase/gitops-github-action).

```yaml
name: Detalii despre runner
on: 
  workflow_dispatch: !!map {}
jobs:
  detaliile-cerute:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
      - name: &obtinere obtinerea-detaliilor
        run: |
          mkdir -p ${{ runner.temp }}/octavian/notite
          cd ${{ runner.temp }}/octavian/notite
          touch -t 202511011030 notita1
          echo Informatii: > notita1
          echo === >> notita1
          uname -r >> notita1
          echo === >> notita1
          cat /etc/*-release >> notita1
          echo === >> notita1
          whoami >> notita1
          echo === >> notita1
          exit 0
      - name: incarcarea-detaliilor
        if: ${{ success() }}
        uses: actions/upload-artifact@v4
        with: 
          name: *obtinere
          path: ${{ runner.temp }}/octavian/notite/notita1
```
