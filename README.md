Nginx vhost for Drupal 7 + PHP-FPM
==================================

*This is an example of Nginx vhost for Drupal 7 + PHP-FPM .*
 
Prereq
------
 
Install NGINX+ PHP-FPM: [HowToForge](http://www.howtoforge.com/installing-nginx-with-php5-and-php-fpm-and-mysql-support-lemp-on-debian-wheezy)


```
Limit acess
 
You can limit access like htaccess / htpasswd on Apache:
 
```
auth_basic "My website Authentication";
auth_basic_user_file /etc/nginx/htpasswd/example.com;
```
