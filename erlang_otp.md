Fix Distributed Erlang port (EPMD on 4369):
```
erl -sname a@osx -setcookie c -kernel inet_dist_listen_min 10000 inet_dist_listen_max 10000
```

IDEs:
* EDTS (Emacs): [MELPA package](https://melpa.org/#/edts).
* distel (Emacs): [incomplete packaging](https://github.com/massemanet/distel/issues/21).
