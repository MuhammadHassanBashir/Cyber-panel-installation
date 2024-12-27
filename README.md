# Cyber-panel-installation

- **For Cyber  panel install/upgrade command follow this github link**: https://github.com/usmannasir/cyberpanel            ##--> remember before installing switch to the root user with this **sudo su -**
- **For Cyber panel installation follow this vedion**: https://www.youtube.com/watch?v=vLmWr3rzKus&list=PLbv4oGGAZQOGC5d3yQBobHXOJZPcmwH0O&index=1
- **link to updgrade cpanel**: https://cyberpanel.net/KnowledgeBase/home/upgrade-cyberpanel/
- **Cpanel official site**: https://cyberpanel.net/
- **how to see cpanel version**: you can see the cpanel version from cpanel WEB console> version management (current verions:   , and build: ). you can also verify this from cpanel vm server path (cat /usr/local/CyberCP/version.txt)
- **how to update cpanel console password**: if your forget cpanel admin console password, but you have access of vm through ssh, then you can update the password using this command **sudo adminPass cpanel**    --> here cpanel is password.. 


## How to Upgrade CyberPanel to a Specific Version. 

      These are the documentation steps. I did this in different way.. job ma cpanel install ker rha tha installation ki command sa like. 
      
         sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)
      
      tb mny installation k time per khub hi minor version diya tha like v2.3.8. jo sahi sa install hogya tha. or phir jb mny usko console sa update kerny ki kosish ki to the major version tu wo ni howa. but mny sable version ki command sa usko update kya tu wo sable version mean 2.3.9 per update hogya... like 
      
         sh <(curl https://raw.githubusercontent.com/usmannasir/cyberpanel/stable/preUpgrade.sh || wget -O - https://raw.githubusercontent.com/usmannasir/cyberpanel/stable/preUpgrade.sh) 
 

These are documentation steps:
-----------------------------

 **wget https://raw.githubusercontent.com/usmannasir/cyberpanel/<branch name>/cyberpanel_upgrade.sh**             --> cpanel ki repo per jakr ap us branch k name dye sakhty hn jis k version ap na cpanel ma install krna ha **like v2.1.2** ... here is repo (https://github.com/usmannasir/cyberpanel)
 
  
  **chmod +x cyberpanel_upgrade.sh**
  
  .**/cyberpanel_upgrade.sh**
  
  Step 1: Remove old script:
  First, you have to remove the old script file to get a new and upgrade. Use the command given below to do this.
  
  rm -rf cyberpanel_upgrade.sh
  
  Step 2: Download specific branch script:
  Now in the next step, you have to download the script for the new branch you want to install using the command stated below.
  
  wget https://raw.githubusercontent.com/usmannasir/cyberpanel/v<branch>/cyberpanel_upgrade.sh
  
  remove <branch> to your required branch name
  
  Step 3: Give execute Permissions :
  
  using the command stated below gives the upgrade command execution permissions.
  
  chmod +x cyberpanel_upgrade.sh
  
  do all this in / or root directory and you must log in as root.
  
  Step 4: Run upgrade script:
  
  Now in the last step just run this command and wait when the system asks for the version give the branch version like “2.0.1-dev”
  
  ./cyberpanel_upgrade.sh
  
  Updates between official versions
  
  Even when there hasn’t been a new version of CyberPanel officially released, there are always minor updates happening behind the scenes. In order to take advantage of these, you can upgrade CyberPanel at any time.


Open source erp next installation link using docker compose
-----------------------------------------------------------

            https://github.com/frappe/erpnext

Steps for deploy Erp next using docker compose
      
      Self-Hosted
      -----------
      
      Docker
      Prerequisites: **docker, docker-compose, git**. Refer Docker Documentation for more details on Docker setup.
      
      Run following commands:
      
      git clone https://github.com/frappe/frappe_docker
      cd frappe_docker
      docker compose -f pwd.yml up -d

      After a couple of minutes, site should be accessible on your localhost port: 8080. Use below default login credentials to access the site.
      
      Username: Administrator
      Password: admin
      
      See Frappe Docker for ARM based docker setup.

Backup
------


Use this command where your erpnext is running, in my case erpnext is running inside my container. so i need to ran this inside the container.

Note: you will get the **file name inside the "sites" folder under file named "common_site_config.json". because i am running erpnext as container. so i would find these details under containers.

  bench --site "sitename" backup --with-files

once done it will show you the backup results like this

    frappe@02317eebfcee:~/frappe-bench$ bench --site frontend backup --with-files
    Backup Summary for frontend at 2024-12-27 19:01:29.692446
    Config  : ./frontend/private/backups/20241227_190122-frontend-site_config_backup.json 94.0B
    Database: ./frontend/private/backups/20241227_190122-frontend-database.sql.gz         1.1MiB
    Public  : ./frontend/private/backups/20241227_190122-frontend-files.tar               10.0KiB
    Private : ./frontend/private/backups/20241227_190122-frontend-private-files.tar       10.0KiB
    Backup for Site frontend has been successfully completed with files


the file backup path would be "/home/frappe/frappe-bench/sites/frontend/private/backups". 

Extracting backup file outside the container
--------------------------------------------

      sudo docker cp 02317eebfcee:/home/frappe/frappe-bench/sites/frontend/private/backups/ ~/erpnext

How to restore the backup:
-------------------------

    In case of any issues and you need to restore the backup, you can follow these steps:

    Step 1: Place the backup files in the container
    First, ensure that the backup files are available inside the container at the same backup directory (private/backups), or you can copy them into the container if they are stored outside.
   
    Step 2: Restore the backup
    To restore the backup, use the following command:

   
          bench --site frontend restore --with-files /path/to/backup-folder
   
    This command will restore the backup for your frontend site.

    /path/to/backup-folder should be the path where your backup files (*.sql.gz for the database, *.tar for files) are located.


    **example**: bench --site frontend restore --with-files /home/frappe/frappe-bench/sites/frontend/private/backups/20241227_190122-frontend-database.sql.gz


erpnext upgration steps
-----------------------
      
      bench switch-to-branch version-15 frappe erpnext --upgrade                           --> agr ap na 14 version run kya howa ha tu is tarha sa 15 upgrade hojye ga..
      
      bench --site "site-name" migrate                     --> domain or get from the sites folder under container
      
      sudo supervisorctl restart all
      
      bench version



