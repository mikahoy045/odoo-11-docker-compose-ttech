# Usage

Install docker for containerisation:
```
$ snap install docker
```

Install nginx:
```
$ sudo apt update
$ sudo apt install nginx
$ systemctl status nginx
```

Change the folder permission to make sure that the container is able to access the directory:
```
$ sudo chmod -R 777 addons
$ sudo chmod -R 777 etc
```

Start the container:
```
$ docker-compose up
```

# Nginx config
- Duplicate default in /etc/nginx/sites-available
```
$ cp /etc/nginx/sites-available/default /etc/nginx/sites-available/odoo11
```
- Proxy pass setup
- Make symlink to sites-enabled
```
$ ln -s /etc/nginx/sites-available/odoo11 /etc/nginx/sites-enabled/
```
- Restart Nginx
```
$ sudo systemctl restart nginx
```

# Odoo Config
* Then locate `localhost:8070` to access Odoo 11.0. If you want to start the server with a different port, change **8070** to another value:

```
ports:
 - "8070:8069"
```

* Log file is printed @ **etc/odoo-server.log**

To run in detached mode, execute this command:

```
$ docker-compose up -d
```

# Custom addons

The **addons** folder contains custom addons. Just put your custom addons if you have any.

# Odoo configuration

To change Odoo configuration, edit file: **etc/odoo.conf**.

# docker-compose.yml

* odoo:11.0
* postgres:9.5

# Screenshots

![odoo-11-welcome-docker](screenshots/odoo-11-welcome-screenshot.png)

![odoo-11-apps-docker](screenshots/odoo-11-apps-screenshot.png)
