```
wget https://artifacts.opensearch.org/releases/bundle/opensearch/2.16.0/opensearch-2.16.0-linux-x64.deb
```

after deb package installation 
	vi  /etc/opensearch/opensearch.yml
	and add this line.
```
plugins.security.disabled: true
```

```
dpkg -i opensearch-2.16.0-linux-x64.deb
```
