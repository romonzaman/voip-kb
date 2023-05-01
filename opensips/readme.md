## opensips

#### setup
```bash
apt-get update -y && apt-get install -y curl wget nano mlocate

```

```bash
curl https://apt.opensips.org/opensips-org.gpg -o /usr/share/keyrings/opensips-org.gpg && \
echo "deb [signed-by=/usr/share/keyrings/opensips-org.gpg] https://apt.opensips.org bullseye 3.2-releases" >/etc/apt/sources.list.d/opensips.list && \
echo "deb [signed-by=/usr/share/keyrings/opensips-org.gpg] https://apt.opensips.org bullseye cli-nightly" >/etc/apt/sources.list.d/opensips-cli.list

```

```bash
apt-get update -y && apt-get install -y default-mysql-server opensips opensips-cli opensips-mysql-module

```
