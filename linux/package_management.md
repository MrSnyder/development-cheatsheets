# Linux package management

## Debian/Ubuntu

### Installing / removing packages

```bash
# install downloaded deb
sudo dpkg -i code_1.51.1-1605051630_amd64.deb
```

### Searching / locating packages

```bash
# list installed packages
dpkg -l | less
# use list to check if docker is installed
dpkg -l docker
sudo dpkg -S docker
# find package for file
dpkg -S /usr/bin/docker
apt-file find /usr/bin/docker
```

### Repositories

[https://linuxize.com/post/how-to-add-apt-repository-in-ubuntu/](https://linuxize.com/post/how-to-add-apt-repository-in-ubuntu/)

