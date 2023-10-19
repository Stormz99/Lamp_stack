Project requirement:
1. Virtualbox 
2. Vagrant

Project explianation:
The Project is orchestrated around creating two Ubuntu virtual machines using Vagrant which are Master and Slave virtual machines which using the LAMP infrastructure (Linux, Apache, mySQL and PHP).

Default configuration on Slave and Master machine:
The Slave and Master machine has a memory of 1024MB and uses 2 C.P.U from the host machine total RAM.

Slave machine information:
1. Slave machine specification: The Slave machine has an host name of "slave_1" with an image name of "ubuntu/focal64". It uses a private network with a constant internet protocol address (ip address) of '192.168.20.11'
2. Slave machine configuration: The slave machine on booting for the first time does a system update and upgrade. This is to allow the system to be at optimal performance. The system also install sshpass which function is to provide password automation for ssh login. The system also install system password authentication from "no" to "yes" which serves as a means of ensuring security to the slave machine in order to checkmate the 'Confidentiality' rule. The slave machine also restarts the systemctl ssh service.

Master machine information:
1. Master machine specification: The Master machine has an host name of "master" with an image name of "ubuntu/focal64". It uses a private network with a constant internet protocol address (ip address) of '192.168.20.10'
2. Master machine configuration: The master machine on booting for the first time does a system update and upgrade. This is to allow the system to be at optimal performance. The system also install sshpass which function is to provide password automation for ssh login. The system also install system password authentication from "no" to "yes" which serves as a means of ensuring security to the master machine in order to checkmate the 'Confidentiality' rule. The master machine also restarts the systemctl ssh service.
3. Script configuration: In the Master machine a sudo user "altschool" is created. A ssh key for user "altschool" is also created. The user "altschool" created in the Master machine is ssh into the Slave machine, only the user "altschool" should be able to ssh into the slave machine without being prompted to input the password. The reason is to ensure security (Confidentiality in the CIA TRIAD). The file named /mnt is copied from the Master machine in "altschool" is copied to the slave machine.

Installation of LAMP stack on the Slave and Master machines:
1. Installing apache2:
sudo apt install apache2 -y or brew install apache2
2. Installing mySQl:
sudo apt install mysql-server -y or brew install mysql
3. Installing php:
sudo apt install php libapache2-mod-php php-mysql -y
4. Enabling modules:
sudo a2enmod rewrite
sudo phpenmod mcrypt
5. Restarting apache:
sudo systemctl reload apache2

After installing the required dependencies, a prompt "LAMP Installation Completed" should be displayed. This confirms that a LAMP stack was installed on both the Slave and Master machine. The apache server is going to be restarted after successful installation. 


