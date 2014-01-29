Nginx vhost for Drupal 7 + PHP-FPM
==================================

*This is an example of Nginx vhost for Drupal 7 + PHP-FPM .*
 
Prereq
------
 
Install NGINX+ PHP-FPM: [HowToForge](http://www.howtoforge.com/installing-nginx-with-php5-and-php-fpm-and-mysql-support-lemp-on-debian-wheezy)



Limit acess
-----------
 
You can limit access like htaccess / htpasswd on Apache:
 
```
auth_basic "My website Authentication";
auth_basic_user_file /etc/nginx/htpasswd/example.com;
```

Phpmyamdin Nginx Config
-----------------------
You can add Phpmyadmin path like that:

```
location /phpmyadmin {
    root /usr/share/;
    index index.php index.html index.htm;
    location ~ ^/phpmyadmin/(.+\.php)$ {
            try_files $uri =404;
            root /usr/share/;
            fastcgi_pass unix:/var/run/php5-fpm.sock;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            include /etc/nginx/fastcgi_params;
    }
    location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
            root /usr/share/;
    }
}

location /phpMyAdmin {
    rewrite ^/* /phpmyadmin last;
}
```
