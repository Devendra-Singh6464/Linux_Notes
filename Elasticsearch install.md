
Check available versions.
```
apt-cache showpkg elasticsearch
```

```
wget [https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.15.2-amd64.deb](https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.15.2-amd64.deb)  
wget [https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.15.2-amd64.deb.sha512](https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.15.2-amd64.deb.sha512)  
shasum -a 512 -c elasticsearch-8.15.2-amd64.deb.sha512  
sudo dpkg -i elasticsearch-8.15.2-amd64.deb
```

install specific version
```
apt-get install elasticsearch=7.10.0
```

how to check elastic search version on your system
```
curl -X GET 'http://localhost:9200'
```

Check Elasticsearch status----
```
sudo /etc/init.d/elaticsearch status
```

If you want to set fix memory to Elasticsearch ----
> So please edit this file-----
```  
vi /etc/elaticsearch/jvm.options
```

```
#Xms4g
#Xms4g 
```

after edit this file restart Elasticsearch service
```
sudo /etc/init.d/elaticsearch start
```
