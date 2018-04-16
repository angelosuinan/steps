# Http and Https Server Setup

### Apache Server

1. Install

```
sudo apt-get install apache2
```

2. Activate this apache modules for proxy of proxy routing

```
sudo -su
a2enmod proxy
a2enmod proxy_http
a2enmod proxy_ajp
a2enmod rewrite
a2enmod deflate
a2enmod headers
a2enmod proxy_balancer
a2enmod proxy_connect
a2enmod proxy_html
```

3. Route port 80 (HTTP) to a web app. Edit 000-default.conf of apache configuration

```
sudo nano /etc/apache2/sites-enabled/000- default.conf
```

4. Remove Document/var/www/html then follow this configuration *port number depends on the web app

```
ProxyPreserveHost On
ProxyPass / http://0.0.0.0:8000/
ProxyPassReverse / http://0.0.0.0:8000/
```

5. Restart and test in the browser [0.0.0.0](0.0.0.0)
```
sudo service apache2 restart
```

#### DNS from noip.com

1. Set an static IP address for your server
2. Enable port forwarding port 80 to server port 80 in the router. Test the external ip address
3. Create a Domain name using [noip.com](noip.com)

#### Configure SSL

Activate SSL module of apache

```
sudo a2enmod ssl
```















