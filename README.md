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
