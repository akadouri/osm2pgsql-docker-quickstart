# osm2pgsql Docker Quickstart

This is a simple docker-compose.yml setup using [osm2pgsql](https://github.com/openstreetmap/osm2pgsql) with [postgis](http://postgis.net/). It is not well tuned, please read the osm2pgsql manual for more information on how to best use osm2pgsql.

# Credit
This project started with a fork from [OsmHackTW/osm2pgsql-docker](https://github.com/OsmHackTW/osm2pgsql-docker) and the version is bumped to 1.3.0. The license from that project is available in this project under osm2pgsql/LICENSE.

At SOTM2022 I learned osm2pgsql is already packaged... so now this container
uses `debian:bookworm-slim` and `osm2pgsql=1.7.0`!

# Usage

Running the following:

```
docker-compose up
```

This will build the osm2pgsql container, download the postgis/postgis image, and run them both. Within the osm2pgsql container is a script to pulldown an OpenStreetMap area from [geofabrik](https://download.geofabrik.de/). The region can be changed in the docker-compose file under `REGION`.

## Extract

If you think you may have to setup your database more than once, consider downloading the
extract from geofabrik, you can specify the pbf directory in under `volumes` in the `docker-compose.yml`. (`delaware` is a great state to test with!)

After the file is loaded into the postgis database, you can connect to it locally with the connection information found in docker-compose.yml

## Updating
You can update the database by re-running the osm2pgsql container, it will use 
`osm2pgsql-replication` to update the existing database.