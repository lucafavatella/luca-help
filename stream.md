## TG La7 in diretta

`open $(curl -sSf https://tg.la7.it/dirette-tv | grep -o "https://stream.la7.it/out/v1/[0-9a-f]\+/index.m3u8" | head -n1)`

### Rationale

```
$ curl -sSf https://tg.la7.it/dirette-tv | grep "\.m3u8"
// var vS = "https://stream.la7.it/out/v1/.../index.m3u8";
var vS = "https://stream.la7.it/out/v1/.../index.m3u8";
      'https://....cloudfront.net/OUT/HLS/Live.m3u8',
```
