# First glance at Docker (Chat app)
## Tech:
- Laravel
- Vue js
- Vite

## Sources:

### YT
https://www.youtube.com/watch?v=3c-iBn73dDE
https://www.youtube.com/watch?v=CkRGJC0ytdU&t=293s

### Docker image for laravel:
https://hub.docker.com/r/bitnami/laravel

## Docker basics

Difference between VM and containers

![docker image](https://miro.medium.com/max/720/0*ujI404Gnomn1Wz5h.webp)

In contrast virtual machines are running on a hypervisor (responsible for running virtual machines) and include it’s own guest operating system. This increased the size of the virtual machines significantly, makes setting up virtual machines more complex and requires more resources to run each virtual machine.

### Images


## Docker commands cheatsheet

`docker-compose build --no-cache` - dont use cache
`docker-compose up --force-recreate` - use fresh containers

`docker exec -it [CONTAINER_ID] bash` - open bash on container
