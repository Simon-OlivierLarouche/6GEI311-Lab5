http {
include mime.types;
default_type application/octet-stream;

#log_format main '$remote_addr - $remote_user [$time_local] "$request"'
#                '$status $body_bytes_sent "$http_referer"'
#                 '"$http_user_agent" "$http_x_forward_for"';
#acces_log logs/acces.log main;

sendfile on;
#tcp_nopush on;
#keepalive_timeout 0;
keepalive_timeout 65;

#gzip on;
upstream labcluster {
  server 198.168.76.124:3000;
  server 198.168.76.82:3001;
  }
  server {
    listen 8181 default_server;
    #listen [::]:8181 default_server;
    #root /var/www/html;
    #server_name _;

    #location /labapp {
      # proxy_pass http://labcluster/labapp;
      #}
  }
  
