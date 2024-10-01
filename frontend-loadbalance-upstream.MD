**keep this folder in linux server path**
##keep under http block##
```
vim /etc/nginx/nginx.conf
```
```
http {
   upstream backend {
      server backend.prasadking.xyz:8080; 
      server backend1.prasadking.xyz:8080;
   }
```

**keep the below block in server path**
```
vim /etc/nginx/default.d/load-balance.conf
```
```
proxy_http_version 1.1;

location /api/ { proxy_pass http://backend/; }

location /health {
  stub_status on;
  access_log off;
}
```