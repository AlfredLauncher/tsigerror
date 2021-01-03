## Ansible Repository

To restore Ansible repository, can be found from github [https://github.com/AAdmiral56/ica0002.git](https://github.com/AAdmiral56/ica0002.git).


## Web servers

To restore web servers, please run the following commands from your management host.

```
ansible-playbook lab04_web_app.yaml
ansible-playbook lab13_haproxy.yaml
```

<br>

## App servers

### Agama
To restore AGAMA, please run the following commands from your management host.

```
ansible-playbook lab02_web_server.yaml
ansible-playbook lab03_web_app.yaml
ansible-playbook lab04_web_app.yaml
ansible-playbook lab13_haproxy.yaml
```

<br>

### Users
To restore users, please run the following command from your management host.

```
ansible-playbook lab02_web_server.yaml
```

<br>

### Docker
To restore docker, please run the following command from your management host.

```
ansible-playbook lab12_docker.yaml
```

In case of any issues, mainly when either Agama or Grafana cannot create an image,enter the commands listed below on the managed host either `vm1`, `vm2` or `vm3`. After executing the commands below, return to the previous chapter and run the playbook again.

```
docker rm <agama or grafana>
docker rmi <agama or grafana/grafana>
```

<br>

## Database

### MySQL
To restore MySQL, please run the following command from your management host.

```
ansible-playbook lab11_mysql_ha.yaml
```
 
 <br>
 
### Agama MySQL database
To restore data in Agama MySQL database, please run the following command from the host machine `vm2`.

```
duplicity --no-encryption restore rsync://aadmiral@backup.adattiva.aadmiral//home/aadmiral56 /home/backup/restore/agama.sql

mysql agama < /home/backuprestore/agama.sql -u agama -p
```

<br>

## Bind and DNS

To restore Bind and DNS, please run the following command from your management host.

```
ansible-playbook lab05_dns.yaml
```

<br>

## Backup

Restoring user `Backup`, please run the following command from your management host.

```
ansible-playbook lab10_backups.yaml
```

<br>

## Monitoring servers

### Prometheus

To restore Prometheus, please run the following command from your management host.

```
ansible-playbook lab06_prometheus.yaml
```

<br>

### Grafana

To restore Grafana, please run the following command from your management host.

```
ansible-playbook lab12_docker.yaml
```

To restore the tables in Grafana, please run the following command from machine `vm3` as backup user.

```
duplicity --no-encryption restore rsync://shrshryo@backup.jetstreamer.ryo//home/shrshryo/ /home/backup/restore/
```

From managed host, run the following code.

```
ansible-playbook lab12_docker.yaml
```

Then as `root` user:

```

cp -a /home/backup/restore/grafana/* /opt/docker/grafana/

chown -R 472:472 /opt/docker/grafana/

docker start grafana
```

<br>

### Telegraf

To restore Telegraf, please run the following command from your management host.

```
ansible-playbook lab08_logging.yaml
```

<br>

### InfluxDB

To restore InfluxDB, please run the following command from your management host.

```
ansible-playbook lab08_logging.yaml
```

<br>

### Pinger

To restore pinger, please run the following command from your management host.

```
ansible-playbook lab08_logging.yaml
```

<br>

### Rsyslog

To restore rsyslog, please run the following command from your management host.

```
ansible-playbook lab08_logging.yaml
```

<br>

### Node exporter

To restore node exporter, please run the following command from your management host.

```
ansible-playbook lab06_prometheus.yaml
```

<br>

### MySQL exporter

To restore MySQL exporter, please run the following command from your management host.

```
ansible-playbook lab07_grafana.yaml
```

<br>

### Nginx exporter

To restore Nginx exporter, please run the following command from your management host.

```
ansible-playbook lab07_grafana.yaml
```

<br>

### Bind exporter

To restore Bind exporter, please run the following command from your management host.

```
ansible-playbook lab07_grafana.yaml
```

<br>

### HAProxy exporter
To restore HAProxy, please run the following command from your management host.

```
ansible-playbook lab13_haproxy.yaml
```

<br>

### keepalived exporter
To restore keepalived, please run the following command from your management host.

```
ansible-playbook lab13_haproxy.yaml
```
