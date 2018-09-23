For checking the presence of a mandatory parameter, insert line:
```
: ${parameter:?}
```

Forward args: `"$@"`

`local R; R=$(...) || exit 1` [local and exit status](http://tldp.org/LDP/abs/html/localvar.html#EXITVALANOMALY01)

[Mimic `set -o pipefail`](http://stackoverflow.com/questions/1221833/bash-pipe-output-and-capture-exit-status/1221844#1221844)
