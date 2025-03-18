# Week 2: Linux System Administration & Automation





## 📌 Task 1: User & Group Management

```markdown
# Creating a new user
sudo useradd -m devops_user

# Viewing user information
cat /etc/passwd

# Setting password for a user
sudo passwd devops_user

# Creating a new group
sudo groupadd devops_team

# Viewing group information
cat /etc/group

# Adding a user to a group
sudo gpasswd -a devops_user devops_team

# Verifying group membership
cat /etc/group

# Granting sudo privileges to a user
sudo usermod -a -G sudo devops_user

# Switching to a user
su - devops_user

# Verifying sudo privileges
sudo whoami  # This will print "root" if sudo privileges are working

# Removing sudo privileges
sudo deluser devops_user sudo
```


## 📌 Task 2: File & Directory Management

```markdown
# Creating a directory
mkdir devops_workspace

# Changing directory
cd devops_workspace

# Creating an empty file
touch project_notes.txt

# Listing files with details
ls -l

# Changing file permissions
chmod 240 project_notes.txt

# Verifying permission changes
ls -l
```


## 📌 Task 3: Log Analysis & Text Processing

```markdown
# Search for "error" in logs
grep -i "error" linux.log 

# Count occurrences of "error"
grep -i "error" linux.log | wc 

# Extract first 3 fields from log
awk '{print $1,$2,$3}' linux.log   # Note: log level was not defined in the log file

# Replace "rhost" with "REDACTED"
sed 's/rhost/REDACTED/g' linux.log

# Redact IP addresses from logs
sed -E 's/[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+/[REDACTED]/g' log_file.txt
# -E enables extended regex
# [0-9]+\.[0-9]+\.[0-9]+\.[0-9]+ matches IPv4 addresses

# Find top 10 most frequent entries
sort | uniq -c | sort -nr | head -10
```


## 📌 Task 4: Volume Management

```markdown
# Create a 6GB logical volume in volume group tws_vg
lvcreate -L 6G -n devops_lv tws_vg

# Display logical volume details
lvdisplay

# Create a mount point
mkdir /mnt/devops_data

# Format the logical volume with ext4 filesystem
mkfs.ext4 /dev/tws_vg/devops_lv

# Mount the logical volume
mount /dev/tws_vg/devops_lv /mnt/devops_data

# Verify the mount
df -h
mount | grep devops_data
```


## 📌 Task 5: Process Management & Backup Script

```markdown
# Display current processes
ps

# Display real-time system performance
top

# Advanced interactive process viewer
htop
```


## 📌 Task 6: Automate Backups with Shell Scripting

```markdown
#!/bin/bash

src=$1
dest=$2

echo "Installing tar ..."
sudo apt install tar -y >/dev/null
echo "Installation Completed..."

echo "Backup for the file Started.."
tar -cvzf $dest/backup_$(date +%F).tar.gz $src
echo "Backup Completed ...."
```

##  Running the Backup Script

```markdown
./backup.sh /home/ubuntu/task2/devops_workspace/ /home/ubuntu/task6/backups
```
##  Setting up a Cron Job

```markdown
# Edit the crontab
crontab -e

# Add this line to run backup daily
* * * * * bash /home/ubuntu/task6/backup.sh /home/ubuntu/task2/devops_workspace/ /home/ubuntu/task6/backups
```

