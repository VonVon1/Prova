## connection to bastion by ssh


- use the following command to connect to bastion 

## HOW TO ACCESS CLUSTER INSTANCE BY SSH

```
1. ssh-add path/to/EGL-dev-key.pem
2. ssh -A <user_instance>@<PublicIP_instances> (bastion ip)
3. ssh <user_instance>@<Cluster_ip> (cluster instance ip)
4. docker exec -it ID_CONTAINER bash
Basic Docker commands:
- To check the started and ID_CONTAINERS containers, use the command "docker ps"
- To check stopped containers, use the command "docker ps -a"
```