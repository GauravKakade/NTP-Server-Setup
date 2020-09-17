# NTP-Server-Setup


use this site for Reference :- https://www.tecmint.com/install-ntp-server-and-client-on-ubuntu/

Steps in the Host PC:
1) sudo apt update -y
2) sudo apt install ntp 
3) sntp --version
4) Now on terminal goto 'sudo nano /etc/ntp.conf' and on this file we need to replace some lines.
from https://www.pool.ntp.org/zone/de you will get the ntp server details for Germany. Copy these 4 lines and paste them instead of the previous ntp server list.
5) sudo systemctl restart ntp
6) sudo systemctl status ntp
7) sudo ufw allow ntp 
* Note - No need of Firewall commands *

Steps in the Client (Turtlebot): 
(All steps can be done with ssh also)
1) sudo apt update -y
2) sudo apt install ntpdate
3) sudo nano /etc/hosts
Here add in the end of file, the IP address and name of the Host PC
For me it was:- '192.168.1.115  LP025'
(use tab for spacing between two) 

4) sudo timedatectl set-ntp off
5) sudo apt install ntp
6) sudo nano /etc/ntp.conf
In the end of this file add this line 'server LP025 prefer iburst'
(LP025 is name of my PC. For you it would change)
7) sudo systemctl restart ntp
8) ntpq -p
