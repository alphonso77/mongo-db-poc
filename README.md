# Mongo DB POC

## Dependencies

### Windows
On Windows, using Chocolatey, all dependencies can be installed by running the following command from an elevated terminal. This will read from the packages.config file which can be updated to preference prior to install. You can also install packages individually, see [Chocolatey Community](https://community.chocolatey.org/packages) to find packages.
> choco install packages.config

* *Docker Desktop*; to install individually: `choco install docker-desktop`
* *Mongo DB Tools*; to install individually: `choco install mongodb-database-tools`

### Mac OSX
For Mac OSX, dependencies can be installed via download, or with Homebrew.
* *Docker Desktop*: `brew install --cask docker`
* *Mongo DB and Tools*: For complete instructions, see:
[https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/)

## Starting the Databases
Start two local running instances of Mongo db in containers.
> docker-compose up

*To run in detached mode, add the option `-d`*

## Connecting to the Databases
Aside from the port, and the connection name, the connection strings below are the same. The two databases can be used for comparison purposes, and regression testing. Legacy ingestion can be performed on one, and v2 ingestion on the other. Automated tests for spot checking can be performed (such as latest invoice date, and number). For a more in-depth analysis, [Studio 3t](https://studio3t.com/knowledge-base/articles/compare-mongodb-collections/) offers some comparison tools.

Using the connection strings below, you can connect with Mongo DB Compass, Studio 3t, or the [Mongo shell](https://docs.mongodb.com/v4.4/mongo/#the-mongo-shell).

### Localhost 27017
> mongodb://localhost:27017/?serverSelectionTimeoutMS=5000&connectTimeoutMS=10000&3t.uriVersion=3&3t.connection.name=localhost&3t.alwaysShowAuthDB=true&3t.alwaysShowDBFromUserRole=true

### Localhost 27018
> mongodb://localhost:27018/?serverSelectionTimeoutMS=5000&connectTimeoutMS=10000&3t.uriVersion=3&3t.connection.name=localhost+mongodb+copy&3t.alwaysShowAuthDB=true&3t.alwaysShowDBFromUserRole=true

## Pull from Dev
Run a single command to pull from the current dev database and restore it to both MongoDB instances locally (27017 & 27018). This uses the `--drop` option which will first drop the local databases before performing a restore.
> npm run pull-dev

## Push Local to Dev
Run a single command to take a dump of the locally runnning server (port 27017 all dbs and collections) and then restore it to `Cluster0` of a Mongo Atlas dev project (Lilypad Dev):
> npm run push-local

## Optional: Connect to the Dev DB Using Mongo Shell
With Mongo Shell installed, run the command:
> mongosh "mongodb+srv://cluster0.h7aky.mongodb.net/lilypaddbv2" --username devuser

Enter the devuser password when prompted.

# Mongo Config File
The config file holds the uri, and password for the dev environment. Note that the password is in the config file and can be shared separately from source control.