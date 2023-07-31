FROM debian:bookworm-slim

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update 
RUN apt-get install -y \
        osm2pgsql \
        postgresql-client-15 \
        osmctools

# clean up
RUN apt-get clean \
        && rm -rf /var/lib/apt/lists/*

ADD ./osm-importer.sh /usr/local/bin/osm-importer.sh
ADD ./custom.style /user/local/bin/custom.style
WORKDIR /osm