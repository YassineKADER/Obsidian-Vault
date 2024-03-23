```
server {
    listen 80;
    server_name proxy.yassinekader.me;

    location / {
        proxy_pass http://127.0.0.1:10000;
        proxy_redirect off;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    access_log /var/log/nginx/v2ray_access.log;
    error_log /var/log/nginx/v2ray_error.log;
}

```

```
{
  "inbounds": [],
  "outbounds": [
    {
      "mux": {
        "enabled": false
      },
      "protocol": "vless",
      "settings": {
        "vnext": [
          {
            "address": "18.206.216.166",
            "port": 443,
            "users": [
              {
                "encryption": "none",
                "flow": "",
                "id": "19796b00-c2ae-11ee-b538-205c6d5f5d78",
                "level": 8
              }
            ]
          }
        ]
      },
      "streamSettings": {
        "grpcSettings": {
          "serviceName": "vlgrpc"
        },
        "network": "grpc",
        "security": "tls",
        "tlsSettings": {
          "allowInsecure": true,
          "serverName": "proxy.yassinekader.me"
        }
      },
      "tag": "VLESS"
    }
  ],
  "policy": {
    "levels": {
      "8": {
        "connIdle": 300,
        "downlinkOnly": 1,
        "handshake": 4,
        "uplinkOnly": 1
      }
    }
  }
}
```
