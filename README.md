# LinuxCommands

## Signature Invalid Error
```
apt-key adv --keyserver hkps://keyserver.ubuntu.com --refresh-keys
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
