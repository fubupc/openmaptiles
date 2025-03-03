# Serve planet on the fly with Tegola

## Prepare

### Clean (Optional)

```bash
make clean          # clean / remove existing build files
docker-compose down # note: this will stop and remove all containers, networks etc.
```

### Generate build files

```bash
make                       # generate build files
```

### Downloads map

```bash
make download area=planet  # download global map data
```

### Setup database and import map data

```bash
make start-db               # start up the database container.
make import-data            # Import external data from OpenStreetMapData, Natural Earth and OpenStreetMap Lake Labels.
make import-osm             # import data into postgres
make import-wikidata        # import Wikidata
make import-sql             # create / import sql functions
```

## Serve tiles

### Start Map Database

```bash
docker-compose up -d postgres
```

### Start Tegola (tile server)

```bash
docker-compose up -d tegola-redis # Start tegola cache redis server
docker-compose up -d tegola-server # Start tegola server to serve tiles
```

### Start tile viewer server

```bash
docker-compose up -d tile-viewer-server
```

## View map in tile viewer

Open [tile viewer](http://localhost:8000/) in browser.
