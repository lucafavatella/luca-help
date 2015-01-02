`:` - see [`dash` man page](http://sources.debian.net/src/dash/0.5.7-4/src/dash.1/#L1093) alongside `true`

`${parameter:?}` - see [`dash` man page](http://sources.debian.net/src/dash/0.5.7-4/src/dash.1/#L916-920).
For cheking the presence of a mandatory parameter, insert line:
```
: ${parameter:?}
```

Forward args: `"$@"`
