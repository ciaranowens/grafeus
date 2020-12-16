# grafeus
Grafana &lt;> Prometheus &lt;> Loki &lt;> Telegraf &lt;> InfluxDB &lt;> AlertManager stack ready to deploy as docker stack.

Grafeus is designed to be easily deployed via CI/CD to different Docker Swarms. The current concept is such that Graefus is deployed per-region, and there are branches that represent the regions of deployment.

## Prerequisites
- If to be accessed externally via URL, appropriately configured load balancer & Cloudflare routing
- Docker swarm cluster (can be a 'babyswarm' if needed)

## Deploying a stack manually
Perhaps for dev/testing, use the following docker compose command:
Edit the config files as you see fit
`docker stack deploy -c docker-compose.yml grafeus`

## Using in CI/CD with primitive tooling
If you have something that can run a very explicit 'docker stack deploy' command on a docker swarm manager node, it is very simple to duplicate the default config folder to be the name of your particular deployment. A simple 'sed' of ./configs/default/ in the docker compose file will on-the-fly sort out your per-region docker compose file.

## AOB
Loosely based on work from stefanprodan/swarmprom. The big change is that I utilise docker configs which means docker container images do not have to be rebuilt for a config change, making it a bit easier to use in terms of "infrastructure as code".

## Why did I reinvent the wheel?
As a consultant, I wanted something I can repurpose for different clients very easily, and allow them to fork this repository.

## Contents
- alertmanager
- prometheus
- grafana
- influxdb
- telegraf
- loki
- unsee
- caddy
- cadvisor
- node-exporter