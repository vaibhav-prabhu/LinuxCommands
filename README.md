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

## Alter EBS Volume in EC2 (Execute the Below as a root user Else use sudo)
```
lsblk

growpart {BLOCK} {PARTITION}
eg:- growpart /dev/xvda 1

For xfs file system
        xfs_growfs -d {FILESYSTEM}

For Ext4 file system
        resize2fs {FILESYSTEM}

```

## Attach EBS to EC2 as a Swap file

```
Check for new volume

lsblk

Set up the swap area

sudo mkswap {Block}
example: - sudo mkswap /dev/xvda

Enable swap
sudo swapon {Block}
example:- sudo swapon /dev/xvda

Make this swap setting persist by adding following line in /etc/fstab
sudo nano /etc/fstab
Content:- {Block} none swap sw 0 0
example:- /dev/xvdf none swap sw 0 0

Check swap space
sudo swapon --show
```

## Resolve the Corrupt ZSH history file
```
cd ~
mv .zsh_history .zsh_history_old
strings .zsh_history_old > .zsh_history
fc -R .zsh_history
```

## Making Git Log output look good
```
git log --graph --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%an%C(reset)%C(bold yellow)%d%C(reset) %C(dim white)- %s%C(reset)' --all
```

## MYSQL Kill all Sleep Queries If Large number of sleep queries are piling up
```
for i in `mysql -u <username> -p<password> <database>  -e "show processlist" | awk '/Sleep/ {print $1}'` ; do mysql -u <username> -p<password> <database>  -e "KILL $i;"; done
```

## Change SSL TLS Ciphers for nginx configuration
```
Nginx Docs for SSL ciphers: - https://nginx.org/en/docs/http/ngx_http_ssl_module.html

SSL Ciphers Naming:- https://www.openssl.org/docs/man1.1.1/man1/ciphers.html

```

## Nginx Logs Format

```
log_format main '$remote_addr - $remote_user [$time_local] "$request" '
                    '$status $body_bytes_sent "$http_referer" '
                    '"$http_user_agent" "$http_x_forwarded_for"';

log_format cloudflare '$http_cf_connecting_ip - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

https://docs.nginx.com/nginx/admin-guide/monitoring/logging/
```
