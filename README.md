# Rocky/Fedora Linux Post Installation Configuration.

A set of productivity tools i usually install on my Rocky/Fedora Linux.

## DNF Configuration

```sh
sudo nano /etc/dnf/dnf.conf
```

Paste the following configurations.

```ini
[main]
gpgcheck=1
installonly_limit=3
clean_requirements_on_remove=True
best=True
skip_if_unavailable=False
max_parallel_downloads=5
fastestmirror=True
defaultyes=True
```

```sh
sudo dnf update
```

## NTFS File System Support

```sh
sudo dnf install epel-release
sudo dnf install ntfs-3g
```

## Media Codecs

```sh
sudo dnf install epel-release rpmfusion-free-release
sudo crb enable
sudo dnf install compat-ffmpeg4 ffmpeg gstreamer1-plugin-openh264 mozilla-openh264 gstreamer1-plugins-ugly
```

## Installing Java

```sh
sudo dnf install java-11-openjdk java-11-openjdk-devel
```

## Installing MySql

```sh
sudo dnf install mysql-community-server
sudo systemctl start mysqld
sudo grep 'temporary password' /var/log/mysqld.log
sudo mysql_secure_installation
sudo grep 'temporary password' /var/log/mysqld.log
```

## Installing PHP

```sh
sudo dnf install php php-cli php-common
sudo dnf install php-mysqlnd
```

## Installing Apache Server

```sh
sudo dnf install httpd
```

## Configuring SELinux

```sh
sudo setsebool -P httpd_can_network_connect=1
sudo setsebool -P httpd_can_network_connect_db 1
```

## Installing MongoDB

```sh
sudo nano /etc/yum.repos.d/mongodb-org-7.0.repo
```

Paste the following configurations

```sh
[mongodb-org-7.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/7.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://pgp.mongodb.com/server-7.0.asc
```

Then

```sh
sudo yum install -y mongodb-org
sudo systemctl start mongod
```

## Installing Nodejs

As npm depends on nodejs so, i am installing npm, Node automatically installed.

```sh
sudo dnf install npm
```

## Installing Inkscape

```sh
sudo dnf install inkscape
```

## Optional Packages

```sh
sudo dnf install zsh
sudo dnf install rpm-build
sudo dnf install neofetch
sudo dnf install neovim
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh
```

## Optional IDE's And Tools

- [VSCode](https://code.visualstudio.com/download)
- [Android Studio](https://developer.android.com/studio)
- [Intellij Idea](https://www.jetbrains.com/idea/download)
- [Php Storm](https://www.jetbrains.com/phpstorm/download)
- [PostMan](https://www.postman.com/downloads)
- [Mongodb Compass](https://www.mongodb.com/try/download/compass)
