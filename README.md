# Ubuntu
configure passwd for root: sudo passwd root\

steps for SSH:\
sudo apt update\
sudo apt install openssh-server openssh-client\
sudo systemctl start ssh\
sudo systemctl enable ssh\
sudo systemctl status ssh\
sudo apt install vim\
sudo vim /etc/ssh/sshd_config\
\
copy semanage\
su -\
semanage port -a -t ssh_port_t -p tcp 65022\
su -l testadmin\
\
sudo systemctl restart sshd\
\
\
\
steps for apache:\
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
useful link: https://linuxhint.com/install_apache_web_server_ubuntu/\
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
GRANT ALL PRIVILEGES ON phpmyadmin.* TO 'phpmyadmin'@'localhost';\
sudo -H vim /etc/apache2/apache2.conf\
Include /etc/phpmyadmin/apache2.conf\
link: https://linuxhint.com/installing_php_myadmin_ubuntu/\
