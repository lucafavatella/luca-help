Show binary info:
```
rabin2 -gAEu -K sha256 foo.exe
```

Show sections with offset and size:
```
radare2 -q -e cfg.fortunes=false -c 'fs sections' -c 'f' foo.exe
```

(
The [recommended way](https://book.rada.re/tools/rabin2/program_sections.html)
of flagging sections seems to show always size (?) 1:
```
printf "%b\n" "$(rabin2 -Sr foo.exe)" "f" | radare2 -q -e cfg.fortunes=false foo.exe
```
)

Attempt to show a section e.g. `.text` hangs:
```
radare2 -q -e cfg.fortunes=false -c 'fs sections' -c 'pD $s{section..text} @section..text' foo.exe
```

Show symbols - and entrypoints - with offset:
```
radare2 -q -e cfg.fortunes=false -c 'fs symbols' -c 'f' foo.exe
```

Show functions with offset and size:
```
radare2 -q -e cfg.fortunes=false -A -c 'fs functions' -c 'f' foo.exe
```

Show functions performing additional experimental analysis
e.g. finding 10% more functions:
```
radare2 -q -e cfg.fortunes=false -AA -c 'fs functions' -c 'f' foo.exe
```

Recursively disassemble symbols:
```
radare2 -q -e scr.color=false -e cfg.fortunes=false -A -c 'fs symbols' -c 'pdr @@ *' foo.exe
```
