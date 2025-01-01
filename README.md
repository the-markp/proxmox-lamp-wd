# proxmox-lamp-wd
Documentation for my WorkDo.io apps running in LAMP LXC in Proxmox.

1. Install Proxmox VE in target nodes
     - Make sure that the nodes have unused identical storage for use with Ceph
3. Configure network for each node
4. Configure NTP for each node - https://pve.proxmox.com/wiki/Time_Synchronization
5. Create cluster
6. Install and configure Ceph
7. Download turnkey LAMP from Proxmox UI
8. Install LAMP and configure virtual server in UI with port 8100
     - Under /etc/apache2/ports.conf, add "Listen 8100"
10. Prepare Apache for Composer:
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
