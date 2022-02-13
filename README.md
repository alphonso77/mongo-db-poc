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

