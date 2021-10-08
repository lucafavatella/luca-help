## Query OSM locally

In order to keep downloaded state in Docker host cache, write `Dockerfile` as follows:
```
# References:
# * https://wiki.openstreetmap.org/w/index.php?title=Overpass_API/Installation&oldid=2198424#Via_a_Docker_image
# * https://wiki.openstreetmap.org/wiki/Overpass_API/versions
# * https://hub.docker.com/r/wiktorn/overpass-api
# * https://github.com/wiktorn/Overpass-API/blob/e4881f5eca786267a077ed4661b9d6a90f1da011/0.7.56.9/Dockerfile#L95
FROM wiktorn/overpass-api:0.7.56.9
ENV OVERPASS_MODE init
ENV OVERPASS_META no
ARG TMP_OVERPASS_PLANET_FILE_PATH=/srv/planet.osm.bz2
RUN curl -f -L -o ${TMP_OVERPASS_PLANET_FILE_PATH} http://download.geofabrik.de/europe/alps-latest.osm.bz2
ENV OVERPASS_PLANET_URL file://${TMP_OVERPASS_PLANET_FILE_PATH}
ENV OVERPASS_DIFF_URL http://download.geofabrik.de/europe/alps-updates/
ENV OVERPASS_USE_AREAS false
ENV OVERPASS_SPACE 4000000000
RUN /app/docker-entrypoint.sh
RUN rm ${TMP_OVERPASS_PLANET_FILE_PATH}
```
then:
```
docker build -t osm-local .
```
then:
```
docker run -p 80:80 osm-local
```

See https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL
e.g.
```
relation["name:it"="Torino"];
relation(around:1000)[boundary=administrative];
(._; >;);
out skel;
```
