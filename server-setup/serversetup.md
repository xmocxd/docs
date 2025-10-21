# init
`adduser xyz`
`usermod -aG sudo xyz` - grant sudo priv

# enable fw
`ufw allow OpenSSH`
`ufw enable` - enable the firewall
`ufw status` - firewall status

# nginx
`apt install nginx`
`ufw app list` - see available apps for fw
`ufw allow 'Nginx Full'`
`systemctl status nginx` - check if nginx is up

# see system ip
`ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'`
