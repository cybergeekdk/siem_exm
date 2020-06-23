OS: Ubuntu

-----------------

apt update
apt upgrade
dpkg-reconfigure tzdata
apt install java-1.8.0-openjdk-devel.x86_64
java
apt install openjdk-11-jre-headless
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list

apt update
apt-get install apt-transport-https
apt install elasticsearch
systemctl daemon-reload
systemctl enable elasticsearch
systemctl start elasticsearch
nano /etc/elasticsearch/elasticsearch.yml

ip address
curl -X GET "10.64.110.15:9200/"
systemctl restart elasticsearch
curl -X GET "10.64.110.15:9200/"

apt install kibana

apt install unzip
cert --keep-ca-key ca --pem --in /root/instance.yml --out /root/certs/certs.zip
bin/elasticsearch-certutil cert --keep-ca-key ca --pem --in /tmp/instance.yml --out /tmp/certs/certs.zip

unzip certs.zip
ls
mkdir -p /etc/elasticsearch/certs
mkdir -p /etc/kibana/certs
cp /tmp/certs/ca/ca.crt /tmp/certs/siem/* /etc/elasticsearch/certs
ls -l /etc/elasticsearch/certs
nano /etc/elasticsearch/elasticsearch.yml

systemctl restart elasticsearch
systemctl status elasticsearch.service
cat /var/log/elasticsearch/elasticsearch.log
nano /etc/elasticsearch/elasticsearch.yml
systemctl start elasticsearch
curl --cacert /etc/elasticsearch/certs/ca.crt -XGET https://siem.domain.dk:9200/_cat/nodes?pretty
cd /usr/share/elasticsearch/
/usr/share/elasticsearch/bin/elasticsearch-setup-passwords interactive
curl --cacert /etc/elasticsearch/certs/ca.crt -XGET https://siem.domain.dk:9200/_cat/nodes?pretty -u elastic
sed  '/^#/d' /etc/kibana/kibana.yml | sed '/^$/d'
ls /etc/kibana/
ip address
nano /etc/kibana/kibana.yml
sed  '/^#/d' /etc/kibana/kibana.yml | sed '/^$/d'
/usr/share/kibana/bin/kibana-keystore create --allow-root
/usr/share/kibana/bin/kibana-keystore add elasticsearch.username --allow-root


