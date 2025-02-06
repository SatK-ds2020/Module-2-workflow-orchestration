# Getting starting with Kestra

### kestra and postgres are setup in docker containers using doker-compose.yaml file in pwd for rest of the project.
```
docker-compose up
```
### To load data to postgres a seperate intsance was created and connected through pgadmin
* reference: dataload-pipeline-postgres/docker-compose.yml
Run Postgres to extract data and put in database

Using pgcli to connect to Postgres
```
$ pgcli -h localhost -p 5432 -u kestra -d de-zoomcamp
```
* yellow_tripdata rows: 14687167
* green_tripdata rows: 6044050

## some examples flow for Kestra understanding
```
docker run --pull=always --rm -it -p 8080:8080 --user=root \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /tmp:/tmp \
  kestra/kestra:latest server local

```
https://kestra.io/docs/tutorial/fundamentals

# created first Flow
Flows are defined in a declarative YAML syntax to keep the orchestration code portable and language-agnostic.

Each flow consists of three required components: id, namespace, and tasks:

1. id represents the name of the flow.
2. namespace can be used to separate development and production environments.
3. tasks is a list of tasks that will be executed in the order they are defined.
Here are those three components in a YAML file:
```
id: getting_started
namespace: company.team
tasks:
  - id: hello_world
    type: io.kestra.plugin.core.log.Log
    message: Hello World!

```
Here is the same flow as before, but this time with labels and descriptions:
```
    id: getting_started
namespace: company.team

description: |
  # Getting Started
  Let's `write` some **markdown** - [first flow](https://t.ly/Vemr0) 🚀

labels:
  owner: rick.astley
  project: never-gonna-give-you-up

tasks:
  - id: hello_world
    type: io.kestra.plugin.core.log.Log
    message: Hello World!
    description: |
      ## About this task
      This task will print "Hello World!" to the logs.

      
  - id: python
    type: io.kestra.plugin.scripts.python.Script
    containerImage: python:slim
    script: |
      print("Hello World!")

```
If you want to comment out some part of your code, use the CTRL + K + C on Windows/Linux

```
id: getting_started
namespace: dev

tasks:
  - id: api
    type: io.kestra.plugin.core.http.Request
    uri: https://dummyjson.com/products

```
Run Postgres to extract data and put in database



