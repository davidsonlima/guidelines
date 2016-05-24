### Configuração

```
user nginx;
worker_processes auto;
error_log /var/log/nginx/error.log;
pid /run/nginx.pid;

events {
    worker_connections  1024;
}

http {
  upstream elasticsearch {
    least_conn;
    server ip1:9200;
    server ip2:9200;
    server ip3:9200;

    keepalive 30;
  }

  server {
    listen 9200;

    location / {
      proxy_pass http://elasticsearch;
      proxy_http_version 1.1;
      proxy_set_header Connection "Keep-Alive";
      proxy_set_header Proxy-Connection "Keep-Alive";
    }


    location ~ ^/_plugin/.*$ {
      proxy_pass http://ip1:9200;
      break;
    }
  }
}
```
