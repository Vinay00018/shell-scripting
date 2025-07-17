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




