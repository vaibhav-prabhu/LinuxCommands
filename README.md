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

## NGINX SITE AUTHENTICATION

```
sudo sh -c "echo -n 'sammy:' >> /etc/nginx/.htpasswd"

sudo sh -c "openssl passwd -apr1 >> /etc/nginx/.htpasswd"

### Add in Root Location Level

        auth_basic "Restricted Content";
        auth_basic_user_file /etc/nginx/.htpasswd; 

```
