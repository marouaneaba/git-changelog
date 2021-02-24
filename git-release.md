## visualiser les commit d'une release:
git log $(git describe --tags --abbrev=0)..HEAD --pretty=format:"%s" -i -E --grep="^(\[INTERNAL\]|\[FEATURE\]|\[FIX\]|\[DOC\])*\[FEATURE\]" > myfile.txt

## récupérer le dernier tag deploye:
git describe --tags --abbrev=0
