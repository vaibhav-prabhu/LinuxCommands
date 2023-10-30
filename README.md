# LinuxCommands

## Signature Invalid Error
```
apt-key adv --keyserver hkps://keyserver.ubuntu.com --refresh-keys
```
### OR
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <KEY>
```

## CHECK the Memory of the datbases
```
SELECT table_schema "Data Base Name", sum( data_length + index_length ) / 1024 / 1024 "Data Base Size in MiB" FROM information_schema.TABLES GROUP BY table_schema;
```
## Cronjobs Settings

```
https://crontab.guru/
```
## Linux Window

```
dbus-run-session -- gnome-shell --nested --wayland
```

## Nginx Site Authenticateion
```
sudo sh -c "echo -n 'sammy:' >> /etc/nginx/.htpasswd"

sudo sh -c "openssl passwd -apr1 >> /etc/nginx/.htpasswd"

### Add in Root Location Level

        auth_basic "Restricted Content";
        auth_basic_user_file /etc/nginx/.htpasswd; 

```

## Convert RSA Key to PEM format
```
ssh-keygen -p -m PEM -f /path/to/id_rsa

openssl rsa -in id_rsa -outform PEM -out id_rsa.pem


```

## Create Certificate Using Certbot
```
sudo apt-get update

sudo apt-get install certbot python3-certbot-nginx

sudo certbot --nginx -d your_domain.com

sudo certbot certonly --webroot -w /path/to/your/nginx/html -d your_domain.com
```

## Make the user not required to enter password when using sudo
```
yourusername ALL=(ALL:ALL) NOPASSWD: ALL
```

## Forgot MYSQL root Passowrd
```
Add the Following the mysqld.cnf file

skip-grant-tables

Restart mysql service

mysql -u root

FLUSH PRIVILEGES;

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

```
