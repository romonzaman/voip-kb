
## node_exporter on debian 111

```
groupadd --system prometheus
useradd -s /sbin/nologin --system -g prometheus prometheus

cd /usr/src/

curl -s https://api.github.com/repos/prometheus/node_exporter/releases/latest| grep browser_download_url|grep linux-amd64|cut -d '"' -f 4|wget -qi -

tar -xvf node_exporter*.tar.gz
cd node_exporter*/
cp node_exporter /usr/local/bin

tee /etc/systemd/system/node_exporter.service <<EOF
[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=default.target
EOF

systemctl daemon-reload
systemctl start node_exporter
systemctl enable node_exporter

systemctl status node_exporter.service

```



>nano /etc/prometheus/prometheus.yml
```
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: "prometheus"
    static_configs:
      - targets: ["localhost:9090"]
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
```

>systemctl restart prometheus

