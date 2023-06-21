# Ubuntu
configure passwd for root: sudo passwd root\
\
steps for SSH:\
sudo apt update\
sudo apt install openssh-server openssh-client\
sudo systemctl start ssh\
sudo systemctl enable ssh\
sudo systemctl status ssh\
sudo apt install vim\
sudo vim /etc/ssh/sshd_config\
sudo systemctl restart ssh\
\
\
\
steps for apache:\
link: https://linuxhint.com/install_apache_web_server_ubuntu/
\
sudo apt install apache2\
sudo ufw app list\
sudo ufw allow ‘OpenSSH’\
sudo ufw status\
sudo systemctl status apache2\
hostname –I\
sudo chown -R $USER:$USER /var/www/html\
sudo chmod -R 755 /var/www/html\
vim /var/www/html/index.html\
sudo systemctl restart apache2\
\
\
\
steps for mariadb: \
sudo apt install mariadb-server\
sudo systemctl start mariadb\
sudo systemctl enable mariadb\
sudo mysql_secure_installation\
\
\
\
steps for phpmyadmin:\
link: https://linuxhint.com/installing_php_myadmin_ubuntu/
\
GRANT ALL PRIVILEGES ON phpmyadmin.* TO 'phpmyadmin'@'localhost';\
sudo -H vim /etc/apache2/apache2.conf\
Include /etc/phpmyadmin/apache2.conf\
\
ssh connection: ssh username@ip -p65022

# CentOS

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
sudo -\
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
