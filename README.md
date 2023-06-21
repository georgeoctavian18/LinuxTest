# LinuxTest

steps for SSH:\
sudo yum update\
sudo yum –y install openssh-server openssh-clients\
sudo systemctl start sshd\
sudo systemctl enable sshd\
sudo systemctl status sshd\
sudo vim /etc/ssh/sshd_config\
\
copy semanage\
su -\
semanage port -a -t ssh_port_t -p tcp 65022\
su -l testadmin\
\
sudo systemctl restart sshd\
\
steps for apache:\
yum install httpd\
cd /etc/httpd\
ls\
cd conf\
cd /var/www\
cd html\
vim index.html\
ifconfig - get the ip address\
systemctl status firewalld - check for status\
systemctl stop firewalld\
systemctl start httpd\
systemctl enable httpd\
\
\
steps for mariadb: \
sudo yum install mariadb-server\
sudo systemctl start mariadb\
sudo systemctl enable mariadb\
sudo mysql_secure_installation\
\
steps for phpmyadmin:\
yum install epel-release\
yum install phpmyadmin\
cd /etc/httpd/conf.d\
vim phpMyAdmin.conf:\
CHANGE Require ip 127.0.0.1 -> Require all granted\
CHANGE Allow from 127.0.0.1 -> Allow from all\
COMMENT Deny from all (first 2)\
sudo yum install php\
systemctl restart httpd\
