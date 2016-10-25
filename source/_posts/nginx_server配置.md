---
title: nginx server conf.conf
permalink: nginx-server-demo
categories:
  - Docs
date: 2015-10-14 13:12:06
tags:
  - nginx
---

[default]
``` bash
server {

listen 8000;
\# listen somename:8080;
\# server_name somename alias another.alias;

location / {
root /www/html;
index index.html index.htm index.php;
autoindex on;
autoindex_exact_size off;
autoindex_localtime on;
}
location ~ \.php$ {
root /www/html;
fastcgi_pass 127.0.0.1:9000;
fastcgi_index index.php;
fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
include fastcgi_params;
}
}
"/etc/nginx/conf.d/virtual.conf" 25L, 594C
```

[/default]