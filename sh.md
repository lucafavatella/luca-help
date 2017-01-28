`:` - see [`dash` man page](http://sources.debian.net/src/dash/0.5.7-4/src/dash.1/#L1093) alongside `true`

`${parameter:?}` - see [`dash` man page](http://sources.debian.net/src/dash/0.5.7-4/src/dash.1/#L916-920).
For cheking the presence of a mandatory parameter, insert line:
```
: ${parameter:?}
```

Forward args: `"$@"`

`local R; R=$(...) || exit 1` [local and exit status](http://tldp.org/LDP/abs/html/localvar.html#EXITVALANOMALY01)

[Mimic `set -o pipefail`](http://stackoverflow.com/questions/1221833/bash-pipe-output-and-capture-exit-status/1221844#1221844)
