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
