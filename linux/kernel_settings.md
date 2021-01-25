# Kernel Settings

## File watches
```sh
# view current limit
cat /proc/sys/fs/inotify/max_user_watches
# increase
sudo su -
echo fs.inotify.max_user_watches=524288 >> /etc/sysctl.conf
sysctl -p
```