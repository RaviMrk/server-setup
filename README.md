# server-setup

# sudo apt update
# sudo apt install nginx
# sudo ufw app list
# sudo ufw allow 'Nginx Full'
# sudo apt install mysql-server
# sudo apt install php-fpm php-mysql

# sudo nano /etc/nginx/sites-available/default

# add this content
```server {
        listen 80 default_server;
        listen [::]:80 default_server;

 index index.html index.php index.htm index.nginx-debian.html;

    location / {
        root /var/www/html/<your UI project dist>;
        try_files $uri $uri/ /index.html;
    }

    location /phpmyadmin {
        root /usr/share/;
        index index.php;

        location ~ ^/phpmyadmin/(.+\.php)$ {
            try_files $uri =404;
            fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            include fastcgi_params;
        }

        location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
            # Root directive not needed here
        }
    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}
```

# sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl

# sudo mysql

# ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password BY '77RuankZuank$Mk@123';

# SELECT user,authentication_string,plugin,host FROM mysql.user;

# exit

# sudo ln -s /usr/share/phpmyadmin /var/www/html/phpmyadmin
# sudo systemctl reload nginx

## create user for database in phpmyadmin

# sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```
bind-address            = 127.0.0.1
update with 
bind-address            = 0.0.0.0
```
# sudo systemctl restart mysql

# curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash

# source ~/.bashrc
# nvm --version
# nvm install 14.15.4
# node --version
# npm --version

# git clone https://github.com/{ownerName}/{repoName}.git

# cd ./directory-name
# npm install

# npm i -g pm2

# pm2 start ./server.js

# nano /etc/nginx/sites-available/default

# nginx -t

# systemctl restart nginx
