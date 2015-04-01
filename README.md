# Setup

## Create and configure a postgres container

```shell
docker run --name postgres-sonarcube -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=sonar -d postgres
```

This will configure a postgres database named 'sonar' for the user 'sonar'

## Create sonar.properties

* Obtain a sonar.properties file and edit it
* Uncomment the jdbc-postgres url and change the host to 'db'
* Set the jdbc-user to 'sonar'
* Set the jdbc-password to the one used in the postgres container
* Obtain a wrapper.conf file 
* Place those file in a volume you want to mount into the container


## Start the Sonar container

```shell
docker run --name sonarcube --link postgres-sonarcube:db -v <config-dir>:/opt/sonarcube/conf -p 9000:9000 -d sonarcube-server
```

