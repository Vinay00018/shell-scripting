# shell-scripting

1. What is Shell Scripting?
-> A script contains sequence of commands to automate tasks such as file manipulation, program execution, and system
   
2. How to Create a Shell Script
#!/bin/bash      # Shebang: Tells system to use bash shell (it tells compiler to what type of script it  is)

3.✅ Shell Script File Permissions in Linux
Every script file has three types of permissions for three categories of users:

👥 User Categories:
Owner (u) – the user who created the file
Group (g) – users in the same group
Others (o) – all other users

🔐 Permission Types:
r – read (view the content)
w – write (modify the content)
x – execute (run the script)monitoring

| Permission | Meaning   | Value |
| ---------- | --------- | ----- |
| r          | Read      | 4     |
| w          | Write     | 2     |
| x          | Execute   | 1     |
| -          | No access | 0     |

### chmod ###
Changes file permissions

✅ Add Permissions:
chmod +x file.sh     # Add execute for all
chmod u+x file.sh    # Add execute for user
chmod g+w file.sh    # Add write for group
chmod o+r file.sh    # Add read for others

❌ Remove Permissions:
chmod -x file.sh     # Remove execute for all
chmod u-w file.sh    # Remove write from user
chmod g-r file.sh    # Remove read from group
chmod o-x file.sh    # Remove execute from others

### chown ###( used to change file ownership)
Linux command used to change the owner and/or group of a file or      directory.
 chown [owner]:[group] filename
 chown vinay:developers file.txt

### Run script ###
./script.sh  

4. Variables
 name="Vinay"
echo "My name is $name"

5.User Input
read -p "Enter your name: " name
echo "Hello $name"

6. Conditional Statements

if [ $age -gt 18 ]; then
  echo "Adult"
else
  echo "Minor"
fi

Operators:
-eq, -ne, -lt, -le, -gt, -ge
==, != (for strings)

📌 What is a Cron Job?
It is a task to run scripts automatically at a scheduled time

1. Create a Shell Script
Example: project.sh

#!/bin/bash
# Generate current timestamp
timestamp=$(date +"%Y-%m-%d_%H-%M-%S")
# Create file with timestamp
touch /home/vinay/scripty/file_$timestamp.txt

Make it executable:
chmod 777 project.sh

2. Add Cron Job
Edit the crontab:
crontab -e
Add this line to run it every minute:

* * * * * /bin/bash /home/vinay/scripty/project.sh
Save and exit (Ctrl + O, Enter, Ctrl + X if using nano).

✅ Confirm Cron is Running
ps -ef | grep cron

✅ Check Cron Logs (Ubuntu)
grep CRON /var/log/syslog

📌 Cron Timing Format
* * * * * command_to_run
│ │ │ │ │
│ │ │ │ └── Day of Week (0 - 6) (Sunday = 0)
│ │ │ └──── Month (1 - 12)
│ │ └────── Day of Month (1 - 31)
│ └──────── Hour (0 - 23)
└────────── Minute (0 - 59)

✅ How to Add Another Cron Job
You don’t need to create a new file — just edit your crontab and add a new line for each job.

🔧 Steps:
Open your crontab:

crontab -e
Add the new job on a new line:

Example:
# Existing job
* * * * * /bin/bash /home/vinay/scripty/project.sh
# New job: Run backup at 1:30 AM daily
30 1 * * * /bin/bash /home/vinay/backup.sh

Save and exit:

In nano: Ctrl + O, Enter, then Ctrl + X

✅ That’s it!
You can add as many jobs as you want, each on its own line.

🔹 crontab Commands for User Cron Jobs
| Command                  | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| `crontab -e`             | Edit the current user’s cron jobs (opens in default editor). |
| `crontab -l`             | List current user’s cron jobs.                               |
| `crontab -r`             | Remove all current user’s cron jobs.                         |
| `crontab -i -r`          | Prompt before removing cron jobs (safer).                    |
| `crontab -u username -l` | View another user's cron jobs (needs sudo).                  |
| `crontab -u username -e` | Edit another user’s cron jobs (needs sudo).                  |

🔹 cron Service Commands
| Command                     | Description                                   |
| --------------------------- | --------------------------------------------- |
| `sudo service cron start`   | Start the cron service.                       |
| `sudo service cron stop`    | Stop the cron service.                        |
| `sudo service cron restart` | Restart the cron service.                     |
| `sudo service cron status`  | Check status of cron service.                 |
| `systemctl status cron`     | Alternative way to check cron service status. |



🔹 View Cron Logs

| Command                     | Description                                     |
| --------------------------- | ----------------------------------------------- |
| `grep CRON /var/log/syslog` | Show cron-related log entries (Ubuntu/Debian).  |
| `tail -f /var/log/syslog`   | Live monitor cron job activity (Ubuntu/Debian). |
