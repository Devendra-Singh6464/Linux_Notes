# Installation for ubuntu linux.
1. create a bash script .
```shell
vi docker.sh
```
2. add this line-
```shell
#!/bin/bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
sudo groupadd docker
```

``` shell
sudo usermod -aG docker <users_name>
apt-get install docker-compose-plugin
docker compose version
```
-  else
```shell
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
3. run docker hello-world container.
```shell
sudo docker run hello-world
```
4. after create script change docker.sh permission and give excute permission.
```shell
chmod +x docker.sh
```
5. go to root run script 
```shell
./docker.sh
```
-`Note `*docker container store in /var/lib/docker/*
### Manage Docker as a non-root user
Create the `docker` group (already created installation time) .
```shell
sudo groupadd docker
```
Add your user to the docker group.
```shell
sudo usermod -aG docker $USER
```
 
 install docker compose
```shell
sudo apt-get update
sudo apt-get install docker-compose-plugin
```
Check docker compose version
```shell
docker compose version
```

- Check all runing and stop containers and images.
```shell
docker ps -a
```
- runing containers only (old way).
```shell
docker conatiner ls
```
- runing images only (old way).
```shell
docker images ls
```
- remove docker image
``` shell
docker rm -f <name_image>
```
- create a container. If `ubuntu` images already in your docker.
- syntax: `docker container run <image_name>`.
- Note: If image not in your machine so this command download the image in docker register.
```Shell
docker container run nginx 
```
- Start docker container 
``` Shell
docker start test-mysql # test-mysql-- container name
```
- How to delete docker container.
```shell
docker container rm <container_id>
```
-  Create a container in background, stop,start,detach container,
- `d989dbff6bbf`: container_ID
```shell
docker container start d989dbff6bbf
```
 * Stop 
```shell
docker container stop <container_ID>
```
- terminate the main process and the container.
`docker kill <container_id>`
```
docker kill nginx
```
- Container run in background in 30 second after 30 second container stop.
- -d : detach
```shell
docker container run -d nginx sleep 30
```
 - pull docker image 
syntax: `docker pull <images_name>`
```shell
docker pull kalilinux/kali-rolling
```
- How to entry docker container.
```shell
docker container run -it kalilinux/kali-rolling /bin/bash
```
- docker container inspect
```shell
docker container inspect <container_id>
```
- check container logs.
```shell
docker container logs <container_id>
```
- check all runing process in side the container.
```shell
docker container top <container_id>
```
- container monitor.
```shell
docker container stats
```
- Docker port mapping, rename container, restart container, exec container
* port forwarding
```shell
docker container run -d -p 3600:8081 nginx
```
- Check the browser  `http://localhost:3600`
- inside the container.
```shell
docker container exec -it <container_id> /bin/bash
```
* rename.
```shell
docker container rename <container_id> <new_name>
```
* Note : for a regular (rootless) user of podman, this file is stored in the `$HOME/.config/containers` directory.
- If you want to set user specific setting so change  `/etc/container/registries.conf`  all configurations but your change this location file that mean changes all container user. if you want to change specific user so `$HOME/.config/containers`  directory.Configuration settings in the override the system-wild-settings in the `/etc/container/registries.conf` file.

*  **1. Unqualified Search Registries**
`unqualified-search-registries = ["docker.io", "quay.io"]`
- **What it does**: If you pull an image without specifying the full registry name (e.g., `nginx` instead of `docker.io/library/nginx`), the system will search for the image in the listed registries, in the order they are specified.
- **Example**:
    - You run `podman pull nginx`.
    - It will first check `docker.io` and then `quay.io` for the `nginx` image.

**2. Prefix and Location**
`# prefix = "example.com/foo" # location = "internal-registry-for-example.net/bar"`

- **What it does**: These settings allow you to map a custom image registry prefix (e.g., `example.com/foo`) to another registry's actual location.
- **Example**:
    - If `prefix = "example.com/foo"` and `location = "internal-registry-for-example.net/bar"`, then pulling `example.com/foo/myimage` will actually pull from `internal-registry-for-example.net/bar/myimage`.

 **3. Mirrors**
`[[registry.mirror]] location = "example-mirror-0.local/mirror-for-foo" [[registry.mirror]] location = "example-mirror-1.local/mirrors/foo" insecure = true`

- **What it does**: Mirrors provide alternate locations for pulling images. If the primary registry is slow or unavailable, the system will try these mirrors in the order listed.
- **Example**:
    - Pulling `example.com/foo/image` will:
        1. Try `example-mirror-0.local/mirror-for-foo/image`.
        2. If the first mirror fails, try `example-mirror-1.local/mirrors/foo/image`.
        3. If all mirrors fail, fall back to the original registry (`example.com/foo/image`).

**4. Insecure Registries**
`insecure = true`

- **What it does**: If `insecure` is set to `true`, the system allows connections to the registry without verifying its TLS (encryption) certificate. This is not recommended for production as it is less secure.
- **Example**:
    - A registry at `http://example.com` (without HTTPS) would work if `insecure = true`.
 **5. Blocking Certain Registries**
`blocked = false`

- **What it does**: If `blocked = true`, pulling images from the specified registry is forbidden.
- **Example**:
    - If `blocked = true` for `example.com/foo`, pulling any image from `example.com/foo` will fail.
**Why Use This Configuration?**

- It improves security by controlling which registries are trusted and how images are resolved.
- It helps avoid ambiguity when pulling images by always specifying a preferred search order or mapping.
- Mirrors ensure availability and speed by using backup locations for images.

 **Practical Takeaways**

- Use `unqualified-search-registries` to define where to search when you don't fully qualify image names.
- Use `prefix` and `location` to redirect image pulls to specific registries.
- Use `mirrors` to improve reliability by adding alternative sources.
- Avoid `insecure = true` unless absolutely necessary for testing.*
 
 **Pull docker mysql image and run mysql container.**
 `Syntax`: `Docker run --name <your_container_name_you_want_to_set> -p<port> <host-machine>:<container> -e MYSQL_ROOT_PASSWORD=<Set_database_login_password> -d <mysql_docker_image_name> `
``` shell
docker run --name mysql-test -p 3306:3307 -e MYSQL_ROOT_PASSWORD=webkul -d mysql-container
``` 