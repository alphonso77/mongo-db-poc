## Starting the Databases
Start two local running instances of Mongo db in containers.
> docker-compose up

*To run in detached mode, add the option `-d`*

## Connecting to the Databases

### Localhost 27017
> mongodb://localhost:27017/?serverSelectionTimeoutMS=5000&connectTimeoutMS=10000&3t.uriVersion=3&3t.connection.name=localhost&3t.alwaysShowAuthDB=true&3t.alwaysShowDBFromUserRole=true

### Localhost 27018
>mongodb://localhost:27018/?serverSelectionTimeoutMS=5000&connectTimeoutMS=10000&3t.uriVersion=3&3t.connection.name=localhost+mongodb+copy&3t.alwaysShowAuthDB=true&3t.alwaysShowDBFromUserRole=true

## Mongo Dump - Dev Restore
Run a single command to take a snapshot of the locally runnning server (port 270117 all dbs and collections) and then restore that snapshot to a Mongo Atlas dev project:
> npm run mongodump-devrestore

## Mongo Dump
To dump a current snapshot of the local database running on port 27017, run the following command from the command line (root of the project):
> mongodump

## Mongo Restore
To restore data from the current Mongo Dump to the Mongo Dev project, run the following command from the command line (root of the project):
> mongorestore --uri mongodb+srv://devuser:EUvuScZLvLVASag9@cluster0.h7aky.mongodb.net

This will read the current dump file, and restore it to `Cluster0` within the `Lilypad Dev` project.

