
## nginx reverse proxy

```
apt-get update -y
apt-get install nginx -y

systemctl status nginx

apt install certbot
certbot certonly --standalone -d domain.com
```

>nano /etc/nginx/sites-enabled/default
```
server {
        listen 443 ssl default_server;

        ssl_certificate /etc/letsencrypt/live/domain.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/domain.com/privkey.pem;

        root /var/www/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name domain.com;

        location / {
                # try_files $uri $uri/ =404;
                proxy_pass http://localhost:3000;
                proxy_buffering off;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-Host $host;
                proxy_set_header X-Forwarded-Port $server_port;
                proxy_set_header Host $http_host;
        }
}
```
