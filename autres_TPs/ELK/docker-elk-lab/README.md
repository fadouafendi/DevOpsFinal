# Docker ELK Lab

This `docker-compose` setup creates an ELK stack for testing. It uses the
following components:

* nginx, to produce logs
* filebeat, an agent to send the nginx logs to logstash
* logstash, to act as a central point to aggregate and parse logs
* elasticsearch, to store parsed log data
* kibana, to inspect and analyse log data

A `logs` volume is used to share the log data between the nginx and filebeat
containers.

An `elasticsearch` volume is used for persisting elasticsearch data.

## Start Stack

```bash
docker-compose up
```

## Use Stack

Browse to `http://localhost:8080` to get an nginx welcome page and start creating
log data.

Browse to `http://localhost:5601` to view kibana. Create an index pattern of
`logstash-*` and view the events.

## Destroy Stack

```bash
# Stop and remove containers
docker-compose down

# Remove state (logs and elasticsearch data)
docker volume rm docker-elk-lab_elasticsearch docker-elk-lab_logs
```
