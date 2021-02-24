-> git config --global -l // pour visualiser la config global, remplacer global par local pour local ....
-> pour git la config local prioritaire de config global, et la config global prioritaire de al config system
---------------------------------------------------------------------------------------------------------------

[user] // user utilisaer dans les description de commit
  email = myemail@mail.com
  name = marouane abakarim
[Push]
  default = simple/upstream // simple permet de pusher que le branch courant, par défault pusher tous les branch modifier en local
[merge]
   tool = vimdiff
[core]
  editor = nvim // editor a utiliser
  pager = less // la visualisation de git log, la place pris par f=git pour la sortie des commands
  excludesfile = /Users/dennish/.gitignore_global // fichier à ignorer plus le fichier .gitignore
[color]
  ui = true
[credential]
  helper = osxkeychain //garder le pasword, pour ne pas re-faire l'authentification à chaque fois
[clean]
  requireForce = false // permet d'éviter d'ajouter le flag -f àchaque fois pour git clean
[alias]
  lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
  wdiff = diff --word-diff //utiliser une diff par word
  wdiffRegex = --word-diff-regex=
  pl = pull --rebase
[help]
    autocorrect = -1 //correction automatique de la command git, (-1) c'est immédiate, le chiffre est incrementale.
[rerere]
    enabled = true //utiliser un cache pour résoudre les conflit, à chaque conflit sauvgarde la correction pour qu'il soit re-utiliser.
[push]
    default = upstream// simple: seule la branche courante sera pusher.
[rebase]
    autosquash = true 
    autostash = true // lors d'une rebase avec des modifications dans le WD, pour ne pas bloquer le rebase git mis le WD dans le stash pour ne pas bloquer le rebase.
[pull]
    rebase = true // git fetch + git rebase 
[diff]
    mnemonicprefix = true // au lieu d'avoir a-b on utiliser i-w (i:index, w: workdirectory)
[difftool "sourcetree"]
  cmd = opendiff \"$LOCAL\" \"$REMOTE\"
[mergetool "sourcetree"]
  cmd = /Applications/SourceTree.app/Contents/Resources/opendiff-w.sh 
  \"$LOCAL\" \"$REMOTE\" -ancestor \"$BASE\" -merge \"$MERGED\"
  trustExitCode = true
git config --global commit.template ~/.gitmessage.txt // permet de préciser la format de commit à utiliser
