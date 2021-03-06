# app-centrale-vindplaats

## Getting started

### Run the application
```
  # Clone this repository
  git clone https://github.com/lblod/app-centrale-vindplaats.git

  # Move into the directory
  cd app-centrale-vindplaats

  # Start the system
  docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d
```

You're application is running and can be queried via http://localhost:4000/sparql, but the database doesn't contain any data yet.

## How to

### Import data in the application
Data can be imported using TTL files. Put the files in `./data/db/toLoad`, remove the data already loaded flag and recreate the `virtuoso` container. For more info, have a look at the [Virtuoso image documentation](https://github.com/tenforce/docker-virtuoso#automatically).

```
  # Stop the virtuoso container
  docker-compose -f docker-compose.yml -f docker-compose.dev.yml stop virtuoso

  # Remove the virtuoso container
  docker-compose -f docker-compose.yml -f docker-compose.dev.yml rm virtuoso
  
  # Remove the data loaded flag
  rm ./data/db/.data_loaded

  # Create the virtuoso container again
  docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d virtuoso
```

Recent data can be downloaded from:
* [Mandatendatabank](https://mandaten.lokaalbestuur.vlaanderen.be/)
* [Leidinggevendendatabank](https://leidinggevenden.lokaalbestuur.vlaanderen.be/)

## Reference
### Data access
The data that is publicly accessible is described in `./config/authorization/config.ex`
