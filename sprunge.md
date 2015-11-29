https://github.com/rupa/sprunge

Upload binary file `$J` to sprunge, and fetch it back avoiding corruption:
```
U=$(cat $J | openssl base64 | curl -F 'sprunge=<-' 'http://sprunge.us') && echo "HINT curl $U | openssl base64 -d > $(basename $J)"
```
