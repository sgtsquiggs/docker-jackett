### No longer maintained! Please use [lsio's image](https://github.com/linuxserver/docker-jackett) instead.

# jackett

This image is derived from [sgtsquiggs/alpine](https://hub.docker.com/r/sgtsquiggs/alpine/).

[Jackett](https://github.com/Jackett/Jackett) works as a proxy server: it translates queries from apps ([Sonarr](https://github.com/Sonarr/Sonarr), [Radarr](https://github.com/Radarr/Radarr), [SickRage](https://sickrage.github.io/), [CouchPotato](https://couchpota.to/), [Mylar](https://github.com/evilhero/mylar), etc) into tracker-site-specific http queries, parses the html response, then sends results back to the requesting software. This allows for getting recent uploads (like RSS) and performing searches. Jackett is a single repository of maintained indexer scraping & translation logic - removing the burden from other apps.

## Usage
```
docker run \
    --name=jackett \
    -v <path to data>:/config \
    -v <path to blackhole>:/downloads \
    -e PGID=<gid> -e PUID=<uid> \
    -p 9117:9117 \
    sgtsquiggs/jackett
```

## Parameters
* `-p 9117:9117` external port 9117 mapping to internal port 9117
* `-v <path>:/config` where configuation files are stored.
* `-v <path>:/downloads` where downloads go.
* `-e PGID=<gid>` for Group ID (see below)
* `-e PUID=<uid>` for User ID (see below)

## User and Group ID
Set these to match the user/group ID of shared data volumes. Files written to these volumes will match the
provided uid/gid.

## Acknowledgements

* [linuxserver/jackett](https://github.com/linuxserver/docker-jackett)
