# Changelog: 

### Expected template:

![img](https://github.com/marouaneaba/git-changelog/blob/develop/changelog_format.png)

#### Qu'est-ce qu'un changelog ?
Un [changelog](https://keepachangelog.com/fr/1.0.0/) est un fichier qui contient une liste triée chronologiquement des changements notables pour chaque version d’un projet.

#### Pourquoi tenir un changelog ?
Pour permettre aux utilisateurs et contributeurs de voir précisément quels changements notables ont été faits entre chaque publication (ou version) d'un projet.

#### Qui a besoin d'un changelog ?
Tout le monde. Qu'ils soient consommateurs ou développeurs, les utilisateurs de logiciels sont des êtres humains qui se soucient de connaître le contenu des logiciels qu'ils utilisent. Quand un logiciel change, ces mêmes personnes veulent savoir comment et pourquoi.

#### Générate changelog commande:
##### les commites se trouve dans la branch Realese:
```
git fecth --prune --all
git log origin/develop..origin/Release-x.y.z-RC1 --oneline --format="%s"
```
##### les commites d'une livraison périodique se trouve dans la production (branch master), la différence entre deux tags master:
```
git log $(git describe --tags --abbrev=0 $(git describe --tags --abbrev=0)^)..$(git describe --tags --abbrev=0) --oneline --format="%s"
```

# Comment écrire un bon message de commit:
Un bon message de commit doit permettre de savoir ce qui a changé et pourquoi. Le comment, c’est à dire la manière d’effectuer ces changements, n’a pas à être expliqué. La lecture du code et la mise en évidence des changements via un diff est explicite en soi.

### Message Structure:

type (scope) : subject

body [Optional]

footer [Optional]

### The Type:

✓ feat: a new feature
✓ fix: a bug fix
✓ docs: changes to documentation
✓ style: formatting, missing semi colons, etc; no code change
✓ refactor: refactoring production code
✓ test: adding tests, refactoring test; no production code change
✓ chore: updating build tasks, package manager configs, etc; no production code change
✓ build : changements qui affectent le système de build ou des dépendances externes (npm, make…)
✓ ci : changements concernant les fichiers et scripts d’intégration ou de configuration (Travis, Ansible, BrowserStack…)
✓ perf : amélioration des performances

### Scope:
Il nous permet immédiatement de savoir quelle partie du projet est affectée/impactée. Par exemple pour un site de e-commerce, on pourrait avoir product, cart ou checkout.

### The Subject:
Une description des modifications apportées. Il ne doit pas dépasser 50 caractères, doit commencer par une majuscule, ne pas se terminer par un point et orionté métier ( langage omni-présent).
Utilisez un ton impératif pour décrire ce que fait un commit plutôt que ce qu'il a fait.

### The Body:
Ils sont donc facultatifs et utilisés uniquement lorsqu'un commit nécessite un peu d'explication et de contexte, expliquer les modifications que vous avez apportées et pourquoi vous les avez effectuées, pourquoi on a créer cette commite on compare avec l'ancien version.
Utilisez le corps pour expliquer le quoi et le pourquoi d'un commite.
Une ligne vierge entre le corps et le sujet est requise et chaque ligne ne doit pas comporter plus de 72 caractères.

On utilise l’impératif présent : add, change, update, remove et non pas changed ou removed.
On explique ici la raison du changement et en quoi c’est nouvelle manière est différente de l’état précédent. Le comment est visible directement dans le code. 

### The Footer:
Le pied de page est également facultatif et principalement utilisé lorsque vous utilisez un outil (JIRA) de suivi des problèmes pour référencer l'ID du problème, on peut mettre le numéro de suivie du sujet.

### Example Commit Message:

feat: Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequenses of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789




### GRUNT:
// TODO why GRUNT or Gulp

### JavaScript:
// TODO why js


### Description:
Git-changelog est un script shell permet de créer une commande changelog. Ceci est utile pour automatiser la production de fichiers changelog. Git-changelog génère des sorties au format markdown ou html.

### Install:
Mettre ce fichier git-changelog dans ton projet.

### Contributing:
- Fork it
- Create your feature branch (git checkout -b my-new-feature)
- Commit your changes (git commit -am 'Add some feature')
- Push to the branch (git push origin my-new-feature)
- Create new Pull Request

### License:
MIT

### Questions and/or Comments:
n'hésitez pas à m'envoyer vos remarques à mar.abakarim@gmail.com
