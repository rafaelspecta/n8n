# n8n with PostgreSQL

## Objective

This repository has the objetive to support the students from the AI classes I teach.

Run n8n locally in the simplest possible way avoiding as much as possible installing unnecesary things on your Operating System.

## Prerequisites

1) Install [Git](https://git-scm.com/downloads)
* Run the instructions on your TERMINAL
* Note on MAC: You might need to install brew first ([instructions](https://brew.sh/))

2) Install [Docker Desktop](https://www.docker.com/)
* Note on Windows: It requires to restart after installing

## Start the application

From your TERMINAL, run the following commands:

1) Download this repositoty
```
git clone https://github.com/rafaelspecta/n8n.git
```
The n8n directory will be created 

2) Enter n8n directory, because every "docker" command must run in that directory
```
cd n8n
```

3) Run the containers (PostgreSQL and n8n appication)
```
docker compose up -d
```

4) Acess n8n on your browser with the following URL
```
http://localhost:5678
```

## Stop the application

When you stop working on it, just stop the containers
```
docker compose stop
```

## Troubleshooting

If you face problems, the logs might be helpful. To check them run
```
docker compose logs -f
```

## Extra

The default name of the database, user and password for PostgreSQL can be changed in the [`.env`](.env) file in the current directory.

## Reference

Based on https://github.com/n8n-io/n8n-hosting/tree/main/docker-compose/withPostgres
