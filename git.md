`git config --local user.email lucafavatella@users.noreply.github.com`

```sh
git filter-branch --env-filter '
OLD_EMAIL="old-email@example.com"
CORRECT_EMAIL="lucafavatella@users.noreply.github.com"
if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]; then
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL"    = "$OLD_EMAIL" ]; then
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' -- master..
```
Ref: https://help.github.com/articles/changing-author-info/

Commands for adding submodule to specific commit:
```
$ git submodule add -b BRANCH https://github.com/FOO/BAR PATH
$ cd PATH
$ git checkout SPECIFICCOMMITHASH
$ cd -
$ git add PATH
$ git commit
```
(Perform on a freshly cloned repo - or previous attempts to use `git submodule` might require usage of `--force` option.)

Commands for updating specific commit of submodule:
```
$ git clone git@github.com:SUPERFOO/SUPERBAR.git
$ cd SUPERBAR
$ git submodule init
$ git submodule update
$ cd PATH
$ git checkout NEWSPECIFICCOMMITHASH ## Put commit hash here.
$ cd -
$ git add PATH
$ git commit
```

```
$ git branch --list -a origin/* | grep -v HEAD | sed 's|^[[:space:]]*remotes/origin/||' | xargs -IXXX git push origin :XXX
```
