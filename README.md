# docker-portainer-ce

Container management in Docker by Portainer. Including settings for the external load balancer Traefik.

# How to use it?

> **NOTE**
>
> You should use this configuration for Portainer together with [this repository](https://github.com/cardinalit/docker-ingress-traefik) for the load balancer Traefik.

1. Clone this repo to your location:
    ```shell script
    $> git clone https://github.com/cardinalit/docker-portainer-ce.git
    $> cd docker-portainer-ce/
    ```
   
2. Copy example files without postfix *example*:
    ```shell script
    $> cp docker-compose.example.yml docker-compose.yml
    ```
   
3. You should export into your system necessary environment for deploy Portainer:
    ```shell script
    $> export PORTAINER_HOST=portainer.your_domain.com
    $> export ROUTER_PREFIX=monitoring
    ```
   where the variables are:
    ```yaml
    PORTAINER_HOST (required)              # Domain for Portainer GUI
    ROUTER_PREFIX  (optional)              # Prefix for router. Makes the router more unique for 
                                           # the load balancer. By default: monitoring
    ```
   
4. Run deploy stack into Docker Swarm:
    ```shell script
    $> docker stack up -c docker-compose.yml monitoring
    ```
   
5. Enjoy with your management system by Portainer!  
Type in your browser `http://${PORTAINER_HOST}`

> **NOTE**
>
> If you don't export **PORTAINER_HOST** environment, by default domain for your installation of Portainer will be  
> `http://portainer.example.com`