# Swarm
> Docker built in orchestration

## Entities
- Managers
- Workers
- Services

## Swarm creation
```bash
# Init a swarm
$ docker swarm init
```
What happened?
- Lots of PKI and security automation
- Raft database created to store root CA, configs and secrets

## Node commands
```bash
# List swarm nodes
$ docker node ls
# Demote one or more nodes from manager in the swarm
$ docker node demote <nodeID> 
# Display information about one or more nodes
$ docker node inspect <nodeID>
# Promote one or more nodes to manager in the swarm
$ docker node promote <nodeID>
# List tasks running on one or more nodes, defaults to current node
$ docker node ps <nodeID>
# Removes one or more nodes from the swarm
$ docker node rm <nodeID>
# Update a node
$ docker node update
```

## Swarm commands
```bash
# Initialize swarm
$ docker swarm init
# Join a swarm as a node and/or manager
$ docker swarm join
# Manage join tokens
$ docker swarm join-token
# Leave a swarm
$ docker swarm leave
# Unlock swarm
$ docker swarm unlock
# Manage the unlock key
$ docker swarm unlock-key
# Update the swarm
$ docker swarm update
```

## Service commands
```bash
# Create a new service from alpine that runs ping
$ docker service create alpine ping 8.8.8.8
# Display detailed info on one or more services
$ docker service inspect <serviceID>
# Fetch the logs of a service
$ docker service logs <serviceID>
# List services
$ docker service ls
# List the tasks of a service
$ docker service ps <serviceID>
# Remove one or more services
$ docker service rm <serviceID>
# Scale one or more replicated services
$ docker service scale <serviceID>
# Update a service to 3 replicas
$ docker service update bold_northcutt --replicas 3
```

## Production grade compose
new `deploy:` key in compose files can't do `build:`
```bash
# Deploy a stack from a compose file
$ docker stack deploy -c <compose_file_name> <stack_name>
# List stacks
$ docker stack ls
```
