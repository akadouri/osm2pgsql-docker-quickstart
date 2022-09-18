FROM debian:bookworm-slim

ENV DEBIAN_FRONTEND=noninteractive
RUN sed -e s%http://archive.ubuntu.com/ubuntu/%mirror://mirrors.ubuntu.com/mirrors.txt% -i /etc/apt/sources.list
RUN apt-get update 
RUN apt-get install -y \
        osm2pgsql=1.7.0 \
        postgresql-client-14 \
        osmctools

# clean up
RUN apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# osm replication script
ADD ./osm-importer.sh /usr/local/bin/osm-importer.sh
ADD ./custom.style /user/local/bin/custom.style
WORKDIR /osm
CMD ["/bin/bash", "-i", "/usr/local/bin/osm-importer.sh"]
