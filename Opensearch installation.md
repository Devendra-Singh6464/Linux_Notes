wget https://artifacts.opensearch.org/releases/bundle/opensearch/2.16.0/opensearch-2.16.0-linux-x64.deb
dpkg -i opensearch-2.16.0-linux-x64.deb
if you facing this issue so.

ERROR: Something went wrong during demo configuration installation. Please see the logs in /var/log/open
search/install_demo_configuration.log
dpkg: error processing package opensearch (--configure):
 installed opensearch package post-installation script subprocess returned error exit status 1
Processing triggers for libc-bin (2.31-0ubuntu9.16) ...
Errors were encountered while processing:
 opensearch
E: Sub-process /usr/bin/dpkg returned an error code (1)
please change configuration in file.

vi  /etc/opensearch/opensearch.yml
and add this line in file.

plugins.security.disabled: true
dpkg -i opensearch-2.16.0-linux-x64.deb
