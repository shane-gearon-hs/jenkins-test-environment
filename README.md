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

## Plugins

These are the main plugins used in this project. Dependencies are also required, see plugins.txt for full list.

- [autostatus](https://github.com/jenkinsci/github-autostatus-plugin)
- [junit](https://github.com/jenkinsci/junit-plugin)

_To get the list of plugins you can run the following in the /var/jenkins_home/plugins dir._

```bash
ls | awk '/\.jpi/{next;} { print $1":latest" }'
```
