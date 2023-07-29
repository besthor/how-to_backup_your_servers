# `HOW TO BACKUP YOUR WEB SERVERS`

`WARNING!!!
THIS IS JUST A SIMPLE AND SHORT GUIDE
I'D ADVISE TO PLEASE PATIENTLY AND CAREFULLY FOLLOW THESE INSTRUCTIONS STEP BY STEP
OR RISK LOOSING ALL THE INSTALLATIONS/CONFIGURATIONS YOU'VE MADE AND PAINFULLY REPEAT THOSE CUMBERSOME TASKS ALL OVER AGAIN`
## `THE CHOICE IS YOURS!`

**If you've received a notification that your web servers will be destroyed soon, it's essential to act quickly and back up your data to ensure you don't lose any valuable information. To back up your servers to your local Ubuntu terminal, you can use the `rsync` command, which is a powerful tool for syncing files between a local and remote location.**



## `Follow these steps to back up your servers to your local Ubuntu terminal:`

- **Open your sandbox or any  terminal**

- **Copy your private and public keys and save them somewhere safe just incase your sandbox will be destroyed too**

- **Go to the alx-system_engineering-devops repository**

`cd alx-system_engineering-devops`
 - **Make a new directory and call it web-servers_backup**

`mkdir web-servers_backup`

- **Go into the new directory**

`cd web-servers_backup`

- **Update your packages**

`sudo apt update`

- **Install rsync**

`sudo apt install -y rsync`

- **Verify if installation was successfully done**

`rsync  --version`

- **Determine Remote Server Connection**

- **FOR EXAMPLE, THESE ARE MY SERVER'S INFORMATION**

`Name		   Username	  IP Addresses 		  State`
`WEB-01	 	ubuntu		   64.301.68.464	  	running`	
`WEB-02		 ubuntu		   92.257.865.139	 	running`	
`LB-01		  ubuntu		   37.932.72.138		  running`


# `HOW TO BACKUP WEB-01`

- **Use the following command and ADD any RELEVANT applications or directories you wish to backup**
- **Such as: nginx, HAproxy, MySQL, UFW, DataDog and so on...**
- **When you run the command, it may prompt for a PASSPHRASE, type in your passhrase (IF you have one) and just continue**

# PLEASE NOTE:
`REPLACE  64.301.68.464  with your WEB-01's IP address`

### Start the Backup for WEB-01

`rsync -avz  ubuntu@64.301.68.464:/etc/nginx :/etc/ufw :/etc/mysql  :/etc/datadog-agent :/var/www  /alx-system_engineering-devops/web-servers_backup/web-01_backup`


# EXTRA INFORMATION
`The options i have used in the above command are as follows:
-a: Archive mode (preserves permissions, ownership, timestamps, etc.).
-v: Verbose output (to see the progress of the upload).
-z: Compresses the data during transfer to speed up the process.`


# `HOW TO BACKUP WEB-02`

- **Use the following command and ADD any RELEVANT applications or directories you wish to backup**
- **Such as: nginx, HAproxy, MySQL, UFW, DataDog and so on...**
- **When you run the command, it may prompt for a PASSPHRASE, type in your passhrase (IF you have one) and just continue**


# `PLEASE NOTE:`
`REPLACE  92.257.865.139  with your WEB-01's IP address`

- **Start the Backup for WEB-02**

`rsync -avz  ubuntu@92.257.865.139:/etc/nginx :/etc/ufw :/etc/mysql  :/etc/datadog-agent :/var/www  /alx-system_engineering-devops/web-servers_backup/web-02_backup`



# `HOW TO BACKUP LB-01`

- **Use the following command and ADD any RELEVANT applications or directories you wish to backup**
- **Such as: nginx, HAproxy, UFW, DataDog and so on...** 


# PLEASE NOTE:
`REPLACE  37.932.72.138  with your LB-01's IP address`

- **When you run the command, it may prompt for a PASSPHRASE, type in your passhrase (IF you have one) and just continue**

- **Start the Backup for LB-01**

`rsync -avz  ubuntu@37.932.72.138:/etc/nginx :/etc/ufw :/etc/haproxy :/etc/letsencrypt  :/etc/ssl  :/etc/datadog-agent  /alx-system_engineering-devops/web-servers_backup/lb-01_backup`

- **You can add a README file**
`echo "web server backup" > README.md`

- **list the files to confirm all files**

`ls `

- **You should see:**

`lb-01_backup  README.md  web-01_backup  web-02_backup`

- **Now git add these files to keep them safe**

`git add lb-01_backup  web-01_backup  web-02_backup && git commit -m "backedup" && git push`

- **After completing these steps, you should have a backup of your server's content on your local Ubuntu terminal and also on your GitHub,
allowing you to access the files even after the server destruction.**



- `If you require additional clarification or help, feel free to send a [mail](igbebestor72gmail.com)
- You can also stay updated with other project guides and Tutorials by following me on **[GitHub](https://github.com/besthor)**
- **Or check out and Subcribe to [My YouTube channel](https://www.youtube.com/channel/UCVLwEYPiV1omTB-8ZQAioyw).**`


## I'll be posting tutorials on how to upload files and applications from your local Ubuntu terminal to your new servers.
- **PLease ensure you don't miss any content by subscribing**
# `Wishing you the best of luck with your server backup process!`


