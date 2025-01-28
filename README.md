# proxmox-lamp-wd
Documentation for my WorkDo.io apps running in LAMP LXC in Proxmox.

1. Install Proxmox VE in target nodes
     - Make sure that the nodes have unused identical storage for use with Ceph
3. Configure network for each node
   Note: to configure WLAN for additional management interface: https://github.com/ThomasRives/Proxmox-over-wifi, then add vmbridge linked to wlo1
5. Configure NTP for each node - https://pve.proxmox.com/wiki/Time_Synchronization
6. Create cluster
7. Install and configure Ceph
8. Download turnkey LAMP from Proxmox UI
   Note: to update the list of available CT templates, run pveam update
10. Install LAMP and configure virtual server in UI with port 8100
     - Under /etc/apache2/ports.conf, add "Listen 8100"
11. Prepare Apache for Composer:
    - sudo a2enmod rewrite
    - sudo systemctl restart apache2
    - sudo nano /etc/apache2/sites-available/000-default.conf
      
     DocumentRoot "/var/www/html"
    <Directory "/var/www/html">
            Options FollowSymLinks
            AllowOverride All
            Require all granted
    </Directory>
12. apt-get install php-curl
13. Create database in LAMP
14. Start WorkDo installation (make sure DB port is set to 3306/default).
