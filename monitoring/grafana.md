## Grafana


```
cd /usr/src/
apt-get install -y adduser libfontconfig1
wget https://dl.grafana.com/enterprise/release/grafana-enterprise_9.4.3_amd64.deb
dpkg -i grafana-enterprise_9.4.3_amd64.deb
```

```
systemctl daemon-reload
systemctl start grafana-server
systemctl enable grafana-server.service
systemctl status grafana-server

```

>nano /etc/default/grafana-server

>nano /etc/grafana/grafana.ini
```
#################################### Server ####################################
[server]
# Protocol (http, https, h2, socket)
protocol = http

# The ip address to bind to, empty will bind to all interfaces
;http_addr =

# The http port  to use
http_port = 3000
```

>systemctl restart grafana-server

To access the Grafana web interface, 
navigate to http://[ip_hostname]:3000 in your web browser. 

Log in with the username "admin" and the password "admin". 
You will be prompted to change your password.

After logging in, go to "Settings" and select "Configurations", 
then choose "Datasources" and select Prometheus.


#### grafana dashboard

Node Exporter Full:

>Dashboards -> imports

```
ID:     1860
```

