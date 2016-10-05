# mosaics-jrc

## Prerequisites
 + JDK8
 + Maven 3.1+

## Build procedure
### Git remarks
as this project relies on git submodules, it is easier to :
 - checkout project all at once using `--recursive`:
 
 ```git clone https://github.com/hilats/mosaics-jrc.git --recursive```
 
 - likewise, when fetching changes, don't forget to retrieve submodule changes using
 
 ```git submodule update --remote```
 
### Maven build
The whole project can be built using maven at the root (note the skipTests, as tests are currently not ported to run anywhere):

```$ mvn install -DskipTests```

As a result, the complete JRC Mosaics app will be available in ./mosaics-jrc-server/target/mosaics-jrc-server-0.1-SNAPSHOT-jar-with-dependencies.jar

## Running

As the jar is runnable, application can be started by simply starting the jar :

```java -jar mosaics-jrc-server/target/mosaics-jrc-server-0.1-SNAPSHOT-jar-with-dependencies.jar``` 

By default, the application requires authentication, and therefore a registration with an OAuth provider.
To start the server while allowing anonymous access, use

```java -Dauth.allowAnonymous=true -jar mosaics-jrc-server/target/mosaics-jrc-server-0.1-SNAPSHOT-jar-with-dependencies.jar```

### Changing port and hostname
By default the server listens on localhost:8080, anough for local development or deploying behind a proxy.
To make the server reachable from the outside or listening to another port, the URL can  be set using the system property ``baseurl``` :

```java -Dbaseurl=http://0.0.0.0:8080 -jar -mosaics-jrc-server/target/mosaics-jrc-server-0.1-SNAPSHOT-jar-with-dependencies.jar``` 

### Troubleshooting

On some platforms (e.g. Ubuntu) the embedded mongo DB instance may throw a `Could not start process: <EOF>` error.
This can be solved by issuing

```export LC_ALL=C```

(See http://stackoverflow.com/questions/19095645/running-mongodb-on-ubuntu)

