# Gitea with Let's Encrypt in a Docker Swarm

Configure Traefik and create secrets for storing the passwords on the Docker Swarm manager node before applying the configuration.

Traefik configuration: https://github.com/heyValdemar/traefik-letsencrypt-docker-swarm

Run `gitea-restore-application-data.sh` on the Docker Swarm worker node where the container for backups is running to restore application data if needed.

Run `gitea-restore-database.sh` on the Docker Swarm node where the container for backups is running to restore database if needed.

Run `docker stack ps gitea | grep gitea_backups | awk 'NR > 0 {print $4}'` on the Docker Swarm manager node to find on which node container for backups is running.

Deploy Gitea in a Docker Swarm using the command:

`docker stack deploy -c gitea-traefik-letsencrypt-docker-swarm.yml gitea`
