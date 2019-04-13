# jenkinsfile-test-pipeline
Test jenkins environment, using docker.

Sets up a Graphana, InfluxDB and Jenkins container.

## Running
Build
```bash
docker-compose build
```

Starting the image

```bash
docker-compose up
```

Reload

```bash
docker-compose rm && docker-compose up
```

This will have your environment up and running, access the services with the below.

- [Jenkins](http://localhost:8080/)
- [Grafana](http://localhost:3000/)

## Setup
### Jenkins
1. Once in Jenkins you need to go to http://localhost:8080/configure and select "Send to Influx", then type in 'http://influx:8086' as the URL and 'jenkins-metrics' as the database. Leave credentials and retention policy blank. (TODO: Automate this)
2. To enable statsd, you also can select "Send to StatsD", then type in 'statsd' as the endpoint and 'service.jenkins_kubernetes.metrics' as the bucket. Leave port and max size at their default values. (TODO: Automate this)

### Influx
Create the database:
```
docker exec jenkins-test-environment_influx_1 influx -execute "create database \"jenkins-metrics\""
```

### Graphana
Load the Graphana dashboard with the password `admin` and username `admin`.
Add a datasource of type Influx DB then type in 'http://influx:8086' as the URL and 'jenkins-metrics' as the database.
Import database `5786` on the 'http://localhost:3000/dashboard/import' page.


## Plugins

These are the main plugins used in this project. Dependencies are also required, see plugins.txt for full list.

- [autostatus](https://github.com/jenkinsci/github-autostatus-plugin)
- [junit](https://github.com/jenkinsci/junit-plugin)

_To get the list of plugins you can run the following in the /var/jenkins_home/plugins dir._

```bash
ls | awk '/\.jpi/{next;} { print $1":latest" }'
```
