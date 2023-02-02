# Changelog: 

L'objectif de ce repositories c'est construire une command git génére du changelog 'git changelog', et encore:
- Exposer la template du configuration git complete.
- Script pour consulter le contenu de la derniére release 

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

```
<header>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```
The `header` is mandatory and must conform to the [Commit Message Header](#commit-header) format.

The `body` is mandatory for all commits except for those of type "docs".
When the body is present it must be at least 20 characters long and must conform to the [Commit Message Body](#commit-body) format.

The `footer` is optional. The [Commit Message Footer](#commit-footer) format describes what the footer is used for and the structure it must have.

Any line of the commit message cannot be longer than 100 characters.

#### <a name="commit-header"></a>Commit Message Header

```
<type>(<scope>): <short summary>
  │       │             │
  │       │             └─⫸ Summary in present tense. Not capitalized. No period at the end.
  │       │
  │       └─⫸ Commit Scope: animations|bazel|benchpress|common|compiler|compiler-cli|core|
  │                          elements|forms|http|language-service|localize|platform-browser|
  │                          platform-browser-dynamic|platform-server|router|service-worker|
  │                          upgrade|zone.js|packaging|changelog|dev-infra|docs-infra|migrations|
  │                          ngcc|ve
  │
  └─⫸ Commit Type: build|ci|docs|feat|fix|perf|refactor|test
```

The `<type>` and `<summary>` fields are mandatory, the `(<scope>)` field is optional.


##### Type

Must be one of the following:

* **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
* **ci**: Changes to our CI configuration files and scripts (example scopes: Circle, BrowserStack, SauceLabs)
* **docs**: Documentation only changes
* **feat**: A new feature
* **fix**: A bug fix
* **perf**: A code change that improves performance
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **test**: Adding missing tests or correcting existing tests


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
Le pied de page est également facultatif et principalement utilisé lorsque vous utilisez un outil (JIRA) de suivi des problèmes pour référencer l'ID du problème, on peut mettre le numéro de suivie du sujet, les PRs relatif ou sera terminer à la fin de cette commit.

The footer can contain information about breaking changes and is also the place to reference GitHub issues, Jira tickets, and other PRs that this commit closes or is related to.

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

### commit.template:
On a la possibilité de définir à la configuration une template sera utiliser comme message du commit, on peut régler ceci sur le chemin d’un fichier de notre système, Git utilisera ce fichier comme message par défaut quand on valide. L’intérêt de créer un modèle de message de validation est que nous pouvons l’utiliser pour se rappeler (ou rappeler aux autres) du format et du style corrects pour créer un message de validation.

```
$ git config --global commit.template ~/.gitmessage.txt
$ git commit
```
[Image template message commit](https://github.com/marouaneaba/git-changelog/blob/develop/template_message_commit.jpg)


### PullRequest_template:
Ajouter une template automatique dans le body du pull request.
[about-issue-and-pull-request-templates](https://docs.github.com/en/github/building-a-strong-community/about-issue-and-pull-request-templates)

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

### Préférences cli:
- https://www.iterm2.com/

- https://github.com/robbyrussell/oh-my-zsh

- https://github.com/romkatv/powerlevel10k

- https://dev.to/abdfnx/oh-my-zsh-powerlevel10k-cool-terminal-1no0?_sm_au_=iVV2kW3fvvWRPPtNVWsfvK70kM0Mc

- https://medium.com/@satriajanaka09/setup-zsh-oh-my-zsh-powerlevel10k-on-ubuntu-20-04-c4a4052508fd

### License:
MIT

### Questions and/or Comments:
n'hésitez pas à m'envoyer vos remarques à mar.abakarim@gmail.com
