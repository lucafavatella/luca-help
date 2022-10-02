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
