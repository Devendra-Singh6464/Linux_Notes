URLs: https://dev.to/wangpin34/how-to-disable-ssl-authencation-of-elasticsearch-46je
https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#_start_a_single_node_cluster

1. Hardened Docker images  
    edit  
    You can also use the hardened Wolfi image for additional security. Using Wolfi images requires Docker version 20.10.10 or higher.

To use the Wolfi image, append -wolfi to the image tag in the Docker command.

```shell
docker pull docker.elastic.co/elasticsearch/elasticsearch-wolfi:8.17.1
```

1.1. Start an Elasticsearch container.

```shell
docker run --name elasticsearch --net elastic -p 9200:9200 -it -m 512MB docker.elastic.co/elasticsearch/elasticsearch-wolfi:8.17.1
```

1.2. SSL Encryption and Authentication can also be disabled via ENV variables. If you start a container with the following both are disabled.

```shell
docker run -d --name elasticsearch01 --net elastic -p 9200:9200 -e "discovery.type=single-node" -e "xpack.security.http.ssl.enabled=false" -e "xpack.security.enabled=false" -e "xpack.security.enrollment.enabled=false" -m 512MB docker.elastic.co/elasticsearch/elasticsearch-wolfi:8.17.1
```

1.3 SSL Encryption and Authentication can also be disabled via ENV variables. If you start a container with the following both are disabled and always restart policy.

```shell
docker run -d --name elasticsearch01 --restart always --net elastic -p 9200:9200 -e "discovery.type=single-node" -e "xpack.security.http.ssl.enabled=false" -e "xpack.security.enabled=false" -e "xpack.security.enrollment.enabled=false" -m 512MB docker.elastic.co/elasticsearch/elasticsearch-wolfi:8.17.1
```

- -d is for detached mode (run the container in the background).
- -it is for interactive mode (to allow interaction with the container's terminal).  
    You shouldn't use both -d and -it together, as they conflict. If you're running the container in detached mode (in the background), you don't need the -it flag.

_Note: After you run this command with out `-d` flag you get elasticsearch username, password and HTTP CA certificate_

```shell
----------------------------------------------------------------------------------------------------
? Elasticsearch security features have been automatically configured!
? Authentication is enabled and cluster connections are encrypted.

??  Password for the elastic user (reset with `bin/elasticsearch-reset-password -u elastic`):
  0sdAJ=lLrr0ogGwBO2vD

??  HTTP CA certificate SHA-256 fingerprint:
  617719cb41234da98f56f2643efa781f01ace6295a4e753e9dbf70c0f90e1419

??  Configure Kibana to use this cluster:
? Run Kibana and click the configuration link in the terminal when Kibana starts.
? Copy the following enrollment token and paste it into Kibana in your browser (valid for the next 30 minutes):
  eyJ2ZXIiOiI4LjE0LjAiLCJhZHIiOlsiMTcyLjE4LjAuMjo5MjAwIl0sImZnciI6IjYxNzcxOWNiNDEyMzRkYTk4ZjU2ZjI2NDNlZmE3ODFmMDFhY2U2Mjk1YTRlNzUzZTlkYmY3MGMwZjkwZTE0MTkiLCJrZXkiOiJPWFhHa1pRQnRuTXR3Rk1pbU8tSjo2cC1aNDNGd1NRNmdCbDI1XzBYcmZ3In0=

?? Configure other nodes to join this cluster:
? Copy the following enrollment token and start new Elasticsearch nodes with `bin/elasticsearch --enrollment-token <token>` (valid for the next 30 minutes):
  eyJ2ZXIiOiI4LjE0LjAiLCJhZHIiOlsiMTcyLjE4LjAuMjo5MjAwIl0sImZnciI6IjYxNzcxOWNiNDEyMzRkYTk4ZjU2ZjI2NDNlZmE3ODFmMDFhY2U2Mjk1YTRlNzUzZTlkYmY3MGMwZjkwZTE0MTkiLCJrZXkiOiJPM1hHa1pRQnRuTXR3Rk1pbU8tTDpiVlRoZmVMalF3V19qOXpGdWJfdFF3In0=

  If you're running in Docker, copy the enrollment token and run:
  `docker run -e "ENROLLMENT_TOKEN=<token>" docker.elastic.co/elasticsearch/elasticsearch:8.17.1`
```

1.4. Copy the http_ca.crt SSL certificate from the container to your local machine.

```shell
wadmin@wadmin34:~$ docker cp elasticsearch:/usr/share/elasticsearch/config/certs/http_ca.crt .
```

output-

```
Successfully copied 3.58kB to /home/wadmin/.
```

1.5. Make a REST API call to Elasticsearch to ensure the Elasticsearch container is running.  
syntax: `curl --cacert http_ca.crt -u elastic:$ELASTIC_PASSWORD https://localhost:9200`

```shell
curl --cacert http_ca.crt -u elastic:0sdAJ=lLrr0ogGwBO2vD https://localhost:9200
```